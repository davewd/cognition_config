# Cognition Schema Documentation

## Overview

The cognition schema provides a standardized way to manage various stages of execution for cognitive tasks that are outsourced to binary execution. This schema is designed to handle any kind of cognitive task configuration, not necessarily limited to code.

## Schema Structure

The cognition configuration consists of three main components:

### 1. cognition_group
- **Type**: String (required)
- **Description**: Name of the cognition group or task category
- **Example**: "Cognition Talus"

### 2. remote_url
- **Type**: String (URI format, required)
- **Description**: Git repository URL where the cognition implementation is stored
- **Example**: "https://github.com/davewd/cognition_talus_mac.git"

### 3. deployment
- **Type**: Object (required)
- **Description**: Deployment configuration for the cognition task
- **Properties**:
  - `github_workflow_names`: Array of strings containing GitHub Actions workflow names to execute

## Usage

### YAML Configuration

Create a `cognition_config.yaml` file with the following structure:

```yaml
cognition_group: "Cognition Talus"
remote_url: "https://github.com/davewd/cognition_talus_mac.git"
deployment:
  github_workflow_names:
    - ""
```

### JSON Configuration

Alternatively, you can use JSON format:

```json
{
  "cognition_group": "Cognition Talus",
  "remote_url": "https://github.com/davewd/cognition_talus_mac.git",
  "deployment": {
    "github_workflow_names": [""]
  }
}
```

## Schema Validation

The configuration can be validated against the JSON schema defined in `cognition_schema.json`.

## Examples

### Example 1: Basic Configuration
```yaml
cognition_group: "Cognition Talus"
remote_url: "https://github.com/davewd/cognition_talus_mac.git"
deployment:
  github_workflow_names:
    - ""
```

### Example 2: Multiple Workflow Names
```yaml
cognition_group: "Cognition Processing"
remote_url: "https://github.com/example/cognition_processor.git"
deployment:
  github_workflow_names:
    - "build-and-test"
    - "deploy-to-staging"
    - "deploy-to-production"
```

## Future Extensions

The schema is designed to be extensible. Future versions may include:
- Execution stages and dependencies
- Environment variables and secrets
- Resource allocation parameters
- Monitoring and logging configuration
- Rollback strategies
