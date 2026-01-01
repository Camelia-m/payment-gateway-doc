# Payment Gateway Documentation

This repository contains the documentation for the Payment Gateway System - a comprehensive microservices-based payment gateway system built with Spring Boot and Spring Cloud Gateway.

## About

This documentation site is built using [MkDocs](https://www.mkdocs.org/), a fast, simple, and downright gorgeous static site generator that's geared towards building project documentation.

The documentation covers:
- System architecture and components
- Service descriptions and responsibilities
- API endpoints and routes
- Authentication and security
- Getting started guides
- Configuration details
- Development guidelines

## Quick Start

### Prerequisites

- **Python**: 3.7 or higher
- **pip**: Python package installer

### Installation

1. **Install MkDocs and Material Theme**

   ```bash
   pip install mkdocs mkdocs-material
   ```

   Or using `requirements.txt` (if available):
   ```bash
   pip install -r requirements.txt
   ```

2. **Serve the Documentation Locally**

   ```bash
   mkdocs serve
   ```

   The documentation will be available at `http://127.0.0.1:8000`

3. **Build Static Site**

   ```bash
   mkdocs build
   ```

   This creates a `site` directory containing the static HTML files ready for deployment.

##  Configuration

The MkDocs configuration is defined in `mkdocs.yml`:

```yaml
site_name: API Documentation
docs_dir: docs
```

### Adding a Theme

To use the Material theme, update `mkdocs.yml`:

```yaml
site_name: API Documentation
docs_dir: docs

theme:
  name: material
  palette:
    primary: indigo
    accent: indigo
  features:
    - navigation.tabs
    - navigation.sections
    - search.suggest
    - search.highlight
```

## Editing Documentation

1. Edit the markdown files in the `docs/` directory
2. Use `mkdocs serve` to preview changes in real-time
3. Changes will automatically reload in your browser

### Adding New Pages

1. Create a new `.md` file in the `docs/` directory
2. Update `mkdocs.yml` to include the new page in the navigation:

```yaml
nav:
  - Home: index.md
  - New Page: new-page.md
```

## Deployment

### GitHub Pages

1. Install the `mkdocs-material` plugin:
   ```bash
   pip install mkdocs-material
   ```

2. Build and deploy:
   ```bash
   mkdocs gh-deploy
   ```

### Other Platforms

After building with `mkdocs build`, deploy the `site/` directory to any static hosting service:
- Netlify
- Vercel
- AWS S3
- Azure Static Web Apps
- Any web server

## Project Structure

```
payment-gateway-doc/
├── docs/                 # Documentation source files
│   └── index.md         # Main documentation
├── mkdocs.yml           # MkDocs configuration
└── README.md            # This file
```

## Related Resources

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Payment Gateway System Documentation](./docs/index.md)

## Contributing

1. Make your changes to the markdown files in `docs/`
2. Test locally using `mkdocs serve`
3. Submit a pull request with your improvements


## Authors

- **k.mirkamali** - Initial work

---

**Note**: This is the documentation repository. For the actual Payment Gateway System implementation, refer to the main project repository.

