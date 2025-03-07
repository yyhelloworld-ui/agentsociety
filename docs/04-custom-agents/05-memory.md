# Memory

```{admonition} Caution
:class: caution
This document is currently under active development. The complete version will be available soon. Stay tuned!
```

There two types of `Memory` in our framework, `StreamMemory` and `StatusMemory`.  
Separating temporal event streams from status information enables efficient memory management and specialized retrieval operations. In an agent, memory is a property and can be called with `agent.memory`.

## memory.stream: `StreamMemory`

`StreamMemory` is used to manage and store time-ordered memory information in a stream-like structure.  
The stream structure mimics natural human memory organization and supports chronological reasoning.

`StreamMemory` stores memories through specialized methods (`add_cognition`, `add_social`, etc.), creating tagged `MemoryNodes` in a capacity-limited `collections.deque`. This structure emulates human memory constraints by automatically removing older entries when full. Each memory receives unique metadata: ID, timestamp, and location context.

Stream memories can be enhanced with cognitive links via `add_cognition_to_memory`, establishing contextual relationships between entries. This associative architecture enables systemic analysis of memory interconnections.

Both direct ID access and semantic search are supported. Using embedding models and similarity algorithms, it performs context-aware queries surpassing basic keyword matching. 

### Usage Example

Use stream memory in your agent.

```python
import asyncio

from agentsociety import Agent, AgentType
from agentsociety.cityagent import memory_config_societyagent
from agentsociety.memory import Memory


class CustomAgent(Agent):
    def __init__(self, name: str,memory:Memory, **kwargs):
        super().__init__(name=name, memory=memory,type=AgentType.Citizen, **kwargs)

    async def forward(
        self,
    ):
        stream = self.memory.stream
        # add stream, type: cognition
        await stream.add_cognition(description="I am a waiter at this restaurant.")
        await stream.add_cognition(description="My working place names as 'A Restaurant'.")
        # relevant search
        await stream.search(query="restaurant")
        # relevant search (within the same day, the time of the Urban Space)
        await stream.search_today(query="restaurant")


async def main():
    extra_attributes, profile, base = memory_config_societyagent()
    agent = CustomAgent(name="name", memory=Memory(extra_attributes, profile, base))
    await agent.forward()


if __name__ == "__main__":
    asyncio.run(main())
```

## memory.status: `StatusMemory`

`StatusMemory` is designed to unify three different types of memory (status, configuration, dynamic) into a single objective memory.  

The design central is the fusion of semantic richness and adaptability. By integrating embedding models and Faiss-based vector search, StatusMemory transcends static storage, transforming raw data into semantically meaningful representations. 

Fields are dynamically contextualized through user-defined templates, allowing textual descriptions to capture deeper relationships between data points. 

### Usage Example

Use status memory in your agent. If you are using `AgentSimulation.run_from_config`, assign your status memory field define function with `ExpConfig.SetAgentConfig(memory_config_func=<STATUS-CONFIG-DICT>)`.

```python
import asyncio

from agentsociety import Agent, AgentType
from agentsociety.cityagent import memory_config_societyagent
from agentsociety.memory import Memory


class CustomAgent(Agent):
    def __init__(self, name: str, memory: Memory, **kwargs):
        super().__init__(name=name, memory=memory, type=AgentType.Citizen, **kwargs)

    async def forward(
        self,
    ):
        status = self.memory.status
        # update value, note that you can not add a new field to status once the memory is instantiated
        await status.update("city", "Beijing")
        # retrieve value
        print(await status.get("city", default_value="New York"))


async def main():
    _, profile, base = memory_config_societyagent()
    # self-define status field
    # key: field name
    # value: tuple(field name, default value, Optional[whether use embedding for this filed])
    extra_attributes = {
        "type": (str, "citizen"),
        "city": (str, "New York", True),
    }
    agent = CustomAgent(name="name", memory=Memory(extra_attributes, profile, base))
    await agent.forward()


if __name__ == "__main__":
    asyncio.run(main())

```



## memory.embedding_model: Embedding Model

To change the embedding model within the `Memory`, you simply need to assign it with `ExpConfig.SetAgentConfig`.


### Usage Example

```python
from agentsociety.configs import (ExpConfig, SimConfig, WorkflowStep,
                                 load_config_from_file)
from agentsociety.llm import SimpleEmbedding

exp_config = ExpConfig(exp_name="test",).SetAgentConfig(
    embedding_model=SimpleEmbedding()
)
```
The incoming `embedding` is an instance of a subclass from `langchain_core.embeddings.Embeddings` and needs to implement `embed_query`, `embed_documents`.  
