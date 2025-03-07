# Changelog

## [1.1.2] - 2025-02-26

### Added
- N/A

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- Calling `syncer` that didn't have time to start causes the gRPC service to report an error.

### Security
- N/A

## [1.1.1] - 2025-02-25

### Added
- N/A

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- Inconsistency of python 3.12 and current pydantic version. 

### Security
- N/A


## [1.1.0] - 2025-02-21

### Added
- N/A

### Changed
- The simulator has been converted to a synchronous mode, controlled by `ExpConfig.SimulatorRequest.steps_per_simulation_step` and `ExpConfig.SimulatorRequest.steps_per_simulation_day` parameters that determine the number of seconds per step for advancing the urban environment time in each simulation step and day.

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A

## [1.0.13] - 2025-02-21

### Added
- N/A

### Changed
- N/A

### Deprecated
- N/A

### Removed
- Delete `enable_institution` in ExpConfig

### Fixed
- N/A

### Security
- N/A

## [1.0.12] - 2025-02-21

### Added
- N/A

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- Document typo on `agentsociety-ui` activation.

### Security
- N/A

## [1.0.11] - 2025-02-21

### Added
- N/A

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- Bug of inconsistent length of `agent_counts` and `agent_class` in `simulation.init_agents`.

### Security
- N/A

## [1.0.10] - 2024-02-21

### Added
- N/A

### Changed
- Example map data download link in the document.

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A

## [1.0.9] - 2024-02-20

### Added
- WeChat group QR code.

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A
  
## [1.0.8] - 2024-02-19

### Added
- N/A

### Changed
- Detailed document.

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A
 
## [1.0.7] - 2024-02-18

### Added
- N/A

### Changed
- Update agentsociety-ui to version v0.3.3.

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A
  
## [1.0.6] - 2024-02-18

### Added
- N/A

### Changed
- Detailed document.

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A
  
## [1.0.5] - 2024-02-15

### Added
- N/A

### Changed
- Set parent_id and lnglat of InstitutionAgent as NULL for pgsql

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A

## [1.0.4] - 2024-02-14

### Added
- N/A

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- Bug of incorrect experiment uid for MLflow tag.

### Security
- N/A

## [1.0.3] - 2024-02-13

### Added
- Social experiment use case document.

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- 

### Security
- N/A

## [1.0.2] - 2024-02-08

### Added
- Social experiment use case with our platform.

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A

## [1.0.1] - 2024-02-07

### Added
- Add `README.md`

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A

## [1.0.0] - 2024-02-06

### Added
- Initial commit.

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A
