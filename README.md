# Kubernetes Operator

Kubernetes operator for managing and automating Kubernetes resources.

## Description

This operator provides automatic management of Kubernetes resources by monitoring their state and performing necessary actions to maintain the desired state.

## Requirements

- Kubernetes cluster (version 1.19+)
- Operator SDK installed in the system
- Go 1.23+ (for development)

## Deployment

### Project Initialization

To start working with the operator, initialize the project:

```bash
cd operator
operator-sdk init --domain <domain> --repo <repo>
```

After initialization, the operator project structure will be created.

### Installation

Installation instructions will be added after the operator is created.

## Technologies

- **Go** - main development language
- **Operator SDK** - framework for creating Kubernetes operators
  - Documentation: https://sdk.operatorframework.io/docs/installation/
  - Version: v1.42.0+

## Operator SDK Installation

### macOS (Homebrew)
```bash
brew install operator-sdk
```

### Linux/Windows
See official documentation: https://sdk.operatorframework.io/docs/installation/

## Project Structure

```
.
├── .cursorrules          # Rules for AI assistant
├── README.md             # This file
├── TEMPLATE.md           # Template project information
├── docs/                 # Documentation
│   └── ...               # Documentation for functions, algorithms, and logic
├── operator/             # Directory for operator initialization
│   └── ...               # Operator structure after initialization
└── ...                   # Other project files
```

## Documentation

Detailed documentation is located in the `docs/` directory:
- [Best Practices](docs/best-practices.md) - Go development best practices
- [Function Rating System](docs/function-rating.md) - System for rating function quality and complexity
- [Operator SDK Guide](docs/operator-sdk-go-guide.md) - Guide to creating Go operators
- [Modules Documentation](docs/modules.md) - Documentation on used modules and dependencies
- [Linting Guide](docs/linting.md) - Code linting with golangci-lint
- [Logging Guide](docs/logging.md) - Logging system documentation
- [Glossary](docs/glossary.md) - Terms and definitions
- Documentation for functions, algorithms, and operator logic

## Development

### Creating the Operator

1. Navigate to the `operator` directory
2. Run initialization: `operator-sdk init --domain <domain> --repo <repo>`
3. Create API and controllers according to Operator SDK documentation

### Local Development

Local development instructions will be added after the operator is created.

## License

This project is licensed under the MIT license.

## Authors

- **Albert Iblyaminov** - creator and main developer
