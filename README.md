# Wellcare Keycloakify Theme

A modern, customizable Keycloak theme built with React and the Keycloakify framework. This project provides a beautiful and user-friendly authentication interface for Keycloak identity and access management.

## 🚀 Features

- **Modern React-based UI**: Built with React 18 and TypeScript for type safety
- **Dual Theme Support**: Custom login and account management themes
- **Internationalization**: Multi-language support for global deployments
- **Storybook Integration**: Interactive component development and testing
- **Hot Reload Development**: Fast development cycle with Vite
- **Automated Builds**: GitHub Actions for continuous integration
- **Customizable Design**: Easy to customize and extend
- **Keycloak Compatibility**: Supports multiple Keycloak versions

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher)
- **pnpm** (v8 or higher) - [Installation guide](https://pnpm.io/installation)
- **Maven** (for building themes) - [Installation guide](https://maven.apache.org/install.html)

### Maven Installation

- **macOS**: `brew install maven`
- **Debian/Ubuntu**: `sudo apt-get install maven`
- **Windows**: `choco install openjdk` and `choco install maven`
- **Manual**: Download from [Maven website](https://maven.apache.org/download.cgi)

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/wellcare/keycloakify.git
   cd keycloakify
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   ```

3. **Start development server**
   ```bash
   pnpm dev
   ```

The development server will start at `http://localhost:5173`

## 🎯 Usage

### Development

```bash
# Start development server with hot reload
pnpm dev

# Run Storybook for component development
pnpm storybook

# Format code
pnpm format

# Build the application
pnpm build
```

### Building Keycloak Theme

```bash
# Build the Keycloak theme JAR files
pnpm build-keycloak-theme
```

This command will:
1. Build the React application
2. Generate JAR files for different Keycloak versions
3. Output files in the `dist` directory

### Testing Locally

For testing specific pages during development, uncomment the mock context in `src/main.tsx`:

```typescript
// Uncomment to test specific pages
import { getKcContextMock } from "./login/KcPageStory";

if (import.meta.env.DEV) {
    window.kcContext = getKcContextMock({
        pageId: "register.ftl",
        overrides: {}
    });
}
```

### Deploying to Keycloak

1. **Build the theme**
   ```bash
   pnpm build-keycloak-theme
   ```

2. **Import to Keycloak**
   - Copy the generated JAR files from `dist/` to your Keycloak's `standalone/deployments/` directory
   - Restart Keycloak
   - Configure the theme in Keycloak Admin Console

For detailed deployment instructions, see the [Keycloakify documentation](https://docs.keycloakify.dev/keycloak-configuration/importing-your-theme-in-keycloak).

## 🏗️ Project Structure

```
keycloakify/
├── src/                    # Source code
│   ├── login/             # Login theme components
│   │   ├── KcContext.ts   # TypeScript context definitions
│   │   ├── KcPage.tsx     # Main login page component
│   │   ├── KcPageStory.tsx # Storybook story for login
│   │   └── i18n.ts        # Internationalization for login
│   ├── account/           # Account management theme components
│   │   ├── KcContext.ts   # TypeScript context definitions
│   │   ├── KcPage.tsx     # Main account page component
│   │   ├── KcPageStory.tsx # Storybook story for account
│   │   └── i18n.ts        # Internationalization for account
│   ├── main.tsx           # Application entry point
│   ├── kc.gen.ts          # Auto-generated Keycloakify types
│   └── vite-env.d.ts      # Vite environment types
├── public/                # Static assets
├── .storybook/            # Storybook configuration
├── docs/                  # Project documentation
├── dist/                  # Build output (generated)
└── package.json           # Dependencies and scripts
```

## 🎨 Customization

### Theme Customization

The project supports multiple customization strategies:

1. **Component Overrides**: Override specific Keycloakify components
2. **Styling**: Customize CSS and styling
3. **Internationalization**: Add new languages and translations
4. **Layout**: Modify page layouts and structure

For detailed customization guides, see the [Keycloakify documentation](https://docs.keycloakify.dev/v/v10/customization-strategies).

### Adding New Pages

1. Create a new component in the appropriate theme directory
2. Add the page to the routing logic in `KcPage.tsx`
3. Create a Storybook story for development
4. Add internationalization strings

## 📚 Documentation

Comprehensive documentation is available in the `docs/` directory:

- **[Architecture](./docs/architecture.md)** - Project structure and design patterns
- **[Dependencies](./docs/dependencies.md)** - Technology stack and libraries
- **[Conventions](./docs/conventions.md)** - Coding standards and best practices
- **[Data Flow](./docs/data-flow.md)** - Data flow patterns and state management
- **[API Reference](./docs/api-reference.md)** - API documentation and integrations
- **[Troubleshooting](./docs/troubleshooting.md)** - Common issues and solutions

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

### Development Setup

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes following the [coding conventions](./docs/conventions.md)
4. Test your changes thoroughly
5. Commit your changes: `git commit -m 'Add some feature'`
6. Push to the branch: `git push origin feature/your-feature-name`
7. Submit a pull request

### Code Standards

- Follow the established [coding conventions](./docs/conventions.md)
- Write meaningful commit messages
- Add tests for new features
- Update documentation as needed
- Ensure all linting checks pass

### Pull Request Process

1. Ensure your code follows the project's coding standards
2. Update documentation if needed
3. Add tests for new functionality
4. Ensure all CI checks pass
5. Request review from maintainers

## 🚀 Deployment

### GitHub Actions

The project includes automated GitHub Actions workflows that:

- Build the theme on every push
- Create releases with JAR artifacts
- Run tests and linting

To enable the workflow:
1. Go to your repository on GitHub
2. Navigate to `Settings` > `Actions` > `Workflow permissions`
3. Select `Read and write permissions`

### Manual Release

To create a new release:

1. Update the version in `package.json`
2. Push the changes
3. GitHub Actions will automatically build and create a release

## 🐛 Troubleshooting

Common issues and solutions are documented in [troubleshooting.md](./docs/troubleshooting.md).

### Common Issues

- **Build failures**: Ensure Maven is properly installed and in PATH
- **Theme not loading**: Check Keycloak logs and JAR deployment
- **Development server issues**: Clear node_modules and reinstall dependencies

## 🔒 Internal Use Only

This project is for internal Wellcare use only. Please do not distribute or use outside of authorized Wellcare environments.

## 🙏 Acknowledgments

- [Keycloakify](https://github.com/keycloakify/keycloakify) - The framework that makes this possible
- [Keycloak](https://www.keycloak.org/) - The identity and access management platform
- [React](https://reactjs.org/) - The UI library
- [Vite](https://vitejs.dev/) - The build tool

## 📞 Support

- **Documentation**: [docs/](./docs/)
- **Issues**: [GitHub Issues](https://github.com/wellcare/keycloakify/issues)
- **Discussions**: [GitHub Discussions](https://github.com/wellcare/keycloakify/discussions)

---

**Made with ❤️ by the Wellcare Team**
