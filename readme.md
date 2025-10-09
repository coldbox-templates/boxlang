<p align="center">
	<img src="https://www.ortussolutions.com/__media/coldbox-185-logo.png">
	<br>
	<img src="https://www.ortussolutions.com/__media/wirebox-185.png" height="125">
	<img src="https://www.ortussolutions.com/__media/cachebox-185.png" height="125" >
	<img src="https://www.ortussolutions.com/__media/logbox-185.png"  height="125">
</p>

<p align="center">
	<a href="https://github.com/ColdBox/coldbox-platform/actions/workflows/snapshot.yml"><img src="https://github.com/ColdBox/coldbox-platform/actions/workflows/snapshot.yml/badge.svg" alt="ColdBox Snapshots" /></a>
	<a href="https://forgebox.io/view/coldbox"><img src="https://forgebox.io/api/v1/entry/coldbox/badges/downloads" alt="Total Downloads" /></a>
	<a href="https://forgebox.io/view/coldbox"><img src="https://forgebox.io/api/v1/entry/coldbox/badges/version" alt="Latest Stable Version" /></a>
	<a href="https://forgebox.io/view/coldbox"><img src="https://img.shields.io/badge/License-Apache2-brightgreen" alt="Apache2 License" /></a>
</p>

<p align="center">
	Copyright Since 2005 ColdBox Platform by Luis Majano and Ortus Solutions, Corp
	<br>
	<a href="https://www.coldbox.org">www.coldbox.org</a> |
	<a href="https://www.ortussolutions.com">www.ortussolutions.com</a>
</p>

----

# 🚀 ColdBox 8 BoxLang Application Template

Welcome to the modern ColdBox 8 BoxLang application template! 🎉 This template provides a solid foundation for building enterprise-grade HMVC (Hierarchical Model-View-Controller) web applications using the BoxLang runtime. Perfect for developers looking to leverage the power of ColdBox with the performance and modern features of BoxLang.

## ⚙️ Requirements

Before getting started, ensure you have the following installed on your operating system:

1. **BoxLang OS** - Operating System Binary
   - 📥 Installation: <https://boxlang.ortusbooks.com/getting-started/installation>
   - 📌 Minimum Version: 1.0+
   - 🎯 Used for: running BoxLang applications and scripts at the operating system level
2. **CommandBox** - CLI toolchain, package manager, and server runtime
   - 📥 Installation: <https://commandbox.ortusbooks.com/setup/installation>
   - 📌 Minimum Version: 6.0+
   - 🎯 Used for: dependency management, server starting, testing, and task automation
3. **Maven** - Java dependency manager (Optional, only if you need Java dependencies)
   - 📥 Installation: <https://maven.apache.org/install.html>
   - 📌 Minimum Version: 3.6+
   - 🎯 Used for: managing Java dependencies if your project requires them


## ⚡ Quick Installation

In order to work with this template, you need to have [CommandBox](https://www.ortussolutions.com/products/commandbox) and the [BoxLang](https://boxlang.ortusbooks.com/) operating system runtime installed on your machine.  CommandBox is the application server of choice for BoxLang applications.  Please note that running BoxLang web applications is different than the BoxLang OS runtime.  The BoxLang OS runtime is used to run BoxLang scripts and command line applications, while CommandBox is used to run web applications.

```bash
# Create a new ColdBox application using this BoxLang template
box coldbox create app --boxlang
# Setup the Template for Operation and preferences
boxlang Setup.bx
# Start up the web server
box server start
```

Your application will be available at `http://localhost:8080` 🌐

Code to your liking and enjoy! 🎊

## 🤖 Setup Script (`Setup.bx`)

After creating your application, run the **Setup.bx** script to configure your template and set your preferences. This interactive script helps you customize your application for your specific needs.

```bash
boxlang Setup.bx
```

### What Setup.bx Does:

The setup script is an **interactive wizard** that walks you through several configuration options to tailor the template to your project needs:

#### 1️⃣ **Environment Configuration** (`.env` file)

- Automatically creates a `.env` file from `.env.example` if it doesn't exist
- Skips creation if `.env` already exists to preserve your settings
- Sets up environment variables for database connections, API keys, and more

#### 2️⃣ **AI Development Assistant** (Copilot Instructions)

- Creates `.github/copilot-instructions.md` for AI-powered coding assistance
- Provides context-aware suggestions based on ColdBox and BoxLang conventions
- Compatible with GitHub Copilot, Cursor, Windsurf, and other AI assistants
- Includes project structure, patterns, and best practices documentation

#### 3️⃣ **Java Dependency Management** (Maven)

- **Prompt**: "Do you want to use Maven for any Java dependency management?"
- **If YES**: Keeps `pom.xml` for managing Java dependencies
  - Add dependencies to the `<dependencies>` section
  - Run `mvn install` to download them to `runtime/lib/`
  - BoxLang automatically class-loads all JARs in that folder
- **If NO**: Removes `pom.xml` and `effective-pom.xml` files

#### 4️⃣ **REST API Configuration**

- **Prompt**: "Is this a REST API only project?"
- **If YES**: Configures your application as a RESTful API
  - Installs production modules: `cbsecurity`, `mementifier`, `cbvalidation`
  - Installs development modules: `route-visualizer`, `relax`
  - Replaces default Router with REST-optimized routing
  - Updates handlers to REST-focused controllers
  - Adds API documentation templates in `resources/apidocs/`
  - Updates tests for API testing patterns
  - Sets default routes to `Echo.index` and `Echo.onError`
- **If NO**: Keeps traditional MVC structure with views and layouts

#### 5️⃣ **Frontend Build System** (Vite)

- **Prompt**: "Do you want to use Vite for your frontend build system?" (Only if not API-only)
- **If YES**: Sets up modern frontend tooling with Vite
  - Copies `vite.config.mjs` configuration
  - Adds `package.json` with Vue 3, Tailwind CSS support
  - Updates `Main.bxm` layout with Vite integration
  - Creates `resources/assets/` directory for CSS/JS
  - Instructions for `npm install`, `npm run dev`, `npm run build`
- **If NO**: Removes Vite-related files

#### 6️⃣ **Docker Containerization**

- **Prompt**: "Do you want to use Docker for containerization?"
- **If YES**: Sets up Docker infrastructure
  - Creates `docker/` directory with Dockerfile
  - Adds `docker-compose.yml` for multi-container setup
  - Includes `.dockerignore` for optimized builds
  - Provides scripts: `docker:build`, `docker:run`, `docker:bash`, `docker:stack`
- **If NO**: Removes Docker files

#### 7️⃣ **Dev Container Support**

- **Prompt**: "Do you want to keep the Dev Container setup so you can code in GitHub?"
- **If YES**: Keeps `.devcontainer/` for VS Code Remote Containers
  - Enables coding in a consistent containerized environment
  - Includes configuration in `.devcontainer/devcontainer.json`
  - Customizable via `.devcontainer/Dockerfile`
- **If NO**: Removes `.devcontainer/` directory

#### 8️⃣ **Cleanup & Finalization**

- Cleans up `box.json` by removing the build ignore array
- Provides helpful next steps and commands
- Optionally remove `Setup.bx` itself after completion

### 🎯 Example Setup Flow:

```bash
$ boxlang Setup.bx
🥊 Creating .env file from .env.example
🥊 Creating .github directory
🥊 Creating copilot file
🙋 Do you want to use Maven for any Java dependency management? (y/n): y
🥊 Setting up a [pom.xml] in your root for Java dependency management
🙋 Is this a REST API only project? (y/n): y
🥊 Setting up a REST API only ColdBox application
🥊 Installing ColdBox API Production Modules: Security, Mementifier, Validation
🥊 Installing ColdBox API Development Modules: route-visualizer,relax
✅ REST API only setup complete!
🙋 Do you want to use Docker for containerization? (y/n): y
🥊 Setting up Docker for containerization
✅ Docker setup complete!
🙋 Do you want to keep the Dev Container setup? (y/n): n
🧹 Cleaning up unnecessary files
🛁 Cleaning up your box.json
🥊 Your ColdBox BoxLang application is ready to roll!
👉 Run 'box server start' to launch the development server.
```>

> **💡 Best Practice**: Run `Setup.bx` immediately after creating your application to ensure everything is configured correctly for your specific use case. You can always modify these choices later by manually adjusting the relevant files.

## ⚡ Vite Frontend Build System

If you chose to use **Vite** during setup, this template includes a modern frontend build system with Vue 3 and Tailwind CSS support. Vite provides lightning-fast hot module replacement (HMR) and optimized production builds.

### 🔧 Vite Configuration

The `vite.config.mjs` file is pre-configured with sensible defaults for ColdBox applications:

```javascript
import { defineConfig } from "vite";
import vue from "@vitejs/plugin-vue";
import tailwindcss from "@tailwindcss/vite";
import coldbox from "coldbox-vite-plugin";

export default defineConfig({
    plugins: [
        coldbox({
            input: [ "resources/assets/css/app.css", "resources/assets/js/app.js" ],
            refresh: true,
            publicDirectory: "public",      // Web root directory
            buildDirectory: "includes"      // Output directory within public
        }),
        vue(),
        tailwindcss()
    ]
});
```

#### 🎯 Key Configuration Options:

- **`input`**: Entry points for CSS and JavaScript files
- **`refresh`**: Enable automatic browser refresh when ColdBox views/layouts change
- **`publicDirectory`**: The web root directory (default: `"public"`)
- **`buildDirectory`**: Where compiled assets are written (default: `"includes"`)
  - Assets output to: `{publicDirectory}/{buildDirectory}/`
  - Example: `public/includes/` with the defaults above

### 📂 Asset Structure:

```text
resources/
└── assets/
    ├── css/
    │   └── app.css          # Main stylesheet (Tailwind)
    └── js/
        └── app.js           # Main JavaScript (Vue 3 app)

public/
└── includes/                # Compiled assets (generated by Vite)
    ├── manifest.json        # Asset manifest for production
    └── assets/
        ├── app-[hash].css   # Compiled & hashed CSS
        └── app-[hash].js    # Compiled & hashed JS
```

### 🚀 Using Vite:

#### Development Mode (Hot Module Replacement):

```bash
npm run dev
```

This starts the Vite development server with HMR at `http://localhost:5173`. The ColdBox application automatically detects the dev server and loads assets from it.

#### Production Build:

```bash
npm run build
```

Compiles and optimizes assets for production, outputting them to `public/includes/`. The generated files include content hashes for cache busting.

### 📝 Including Assets in Views:

The `vite()` helper function automatically loads assets based on the environment:

```boxlang
<!--- In your Main.bxm layout --->
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    #vite([
        "resources/assets/css/app.css",
        "resources/assets/js/app.js"
    ])#
</head>
```

**Development**: Loads from Vite dev server (`http://localhost:5173`)
**Production**: Loads compiled assets from `public/includes/assets/`

### 🎨 Customizing Vite:

#### Change Output Directory:

```javascript
coldbox({
    input: [ "resources/assets/css/app.css", "resources/assets/js/app.js" ],
    refresh: true,
    publicDirectory: "public",
    buildDirectory: "dist"      // Assets output to public/dist/
})
```

#### Add More Entry Points:

```javascript
coldbox({
    input: [
        "resources/assets/css/app.css",
        "resources/assets/js/app.js",
        "resources/assets/js/admin.js",     // Additional JS entry
        "resources/assets/css/admin.css"    // Additional CSS entry
    ],
    refresh: true
})
```

#### Configure Refresh Paths:

```javascript
coldbox({
    input: [ "resources/assets/css/app.css", "resources/assets/js/app.js" ],
    refresh: [
        "app/layouts/**",
        "app/views/**",
        "app/config/Router.bx",
        "app/handlers/**/*.bx"   // Also refresh on handler changes
    ]
})
```

> **📚 Learn More**: Check out the [coldbox-vite-plugin documentation](https://github.com/coldbox/coldbox-vite-plugin) and [Vite documentation](https://vitejs.dev) for advanced configuration options.

## 📦 Build Script (`Build.bx`)

The **Build.bx** script compiles and packages your application for distribution. It creates optimized, production-ready builds that can be deployed to any environment.

```bash
boxlang Build.bx
```

### What Build.bx Does:

The build process performs the following steps:

1. **🧹 Clean Build Directory**: Removes any existing `build/` folder and creates a fresh structure
2. **📁 Copy Sources**: Copies application files (`app/`, `modules/`, `public/`, `runtime/`) to the build package
3. **⊘ Smart Exclusions**: Automatically excludes:
   - Log files and directories (`logs/`, `*.log`)
   - System files (`.DS_Store`, `Thumbs.db`)
   - Hidden files and folders (`.git`, `.gitignore`, etc.)
4. **🏷️ Build ID**: Creates a build information file with project name, version, and timestamp
5. **🔨 Compilation**: Compiles BoxLang sources in `app/` and `public/` to optimized bytecode
6. **📦 Distribution Package**: Creates a ZIP file: `build/distributions/{projectName}-{projectVersion}.zip`
7. **🔐 Checksums**: Generates security checksums (MD5, SHA-256, SHA-512) for integrity verification

### Build Output Structure:

```text
build/
├── package/                          # Staged files ready for distribution
│   ├── app/                         # Compiled application code
│   ├── modules/                     # Application modules
│   ├── public/                      # Compiled public assets
│   ├── runtime/                     # Runtime configuration (without logs)
│   └── {projectName}-{version}.md   # Build information
└── distributions/                    # Final distribution files
    ├── {projectName}-{version}.zip
    ├── {projectName}-{version}.zip.md5
    ├── {projectName}-{version}.zip.sha256
    └── {projectName}-{version}.zip.sha512
```

### Customizing the Build:

You can customize what gets included or excluded by editing the `Build.bx` file's initialization section. The build script uses two configurable arrays:

#### 📦 **Sources Array** - What to Include

Controls which directories and files get packaged in your distribution:

```boxlang
// Source directories to package
variables.sources = [
    ".cbmigrations.json",  // Database migrations state
    "box.json",            // Project metadata
    "app",                 // Your ColdBox application
    "modules",             // Installed modules
    "public",              // Web root with assets
    "runtime"              // BoxLang runtime config
];
```

**To add more sources**, simply append to the array:

```boxlang
variables.sources = [
    ".cbmigrations.json",
    "box.json",
    "app",
    "modules",
    "public",
    "runtime",
    "config",              // Add custom config directory
    "resources/database"   // Include database resources
];
```

#### 🚫 **Excludes Array** - What to Skip

Uses **regex patterns** to exclude files/directories from the build:

```boxlang
// Files and folders to exclude from the build (regex patterns)
variables.excludes = [
    "logs/",           // Log directories
    "\.DS_Store$",     // macOS system files
    "Thumbs\.db$"      // Windows system files
];
```

**Common exclusion patterns**:

```boxlang
variables.excludes = [
    "logs/",              // Exclude all log directories
    "\.log$",             // Exclude .log files
    "\.tmp$",             // Exclude .tmp files
    "test-results/",      // Exclude test output
    "node_modules/",      // Exclude npm dependencies
    "\.git",              // Exclude git repository
    "\.env",              // Exclude environment files
    "\.bak$",             // Exclude backup files
    "resources/vite/",    // Exclude vite resources after setup
    "resources/rest/"     // Exclude rest resources after setup
];
```

**Regex Pattern Tips**:
- Use `$` to match end of string: `\.log$` matches files ending in `.log`
- Use `/` to match directories: `logs/` matches any `logs` directory
- Use `\.` to escape dots: `\.DS_Store$` matches `.DS_Store` files
- Use `.*` for wildcards: `temp.*` matches anything starting with `temp`

#### 🔧 **Example: Custom Build Configuration**

```boxlang
function init(){
    // ... existing code ...

    // Custom sources for your project
    variables.sources = [
        ".cbmigrations.json",
        "box.json",
        "app",
        "modules",
        "public",
        "runtime",
        "custom-config",        // Add your custom directory
        "static-files"          // Add static file directory
    ];

    // Comprehensive exclusions
    variables.excludes = [
        "logs/",                // No log files
        "\.DS_Store$",          // No macOS files
        "Thumbs\.db$",          // No Windows files
        "test-results/",        // No test outputs
        "\.env\..*",            // No environment files
        "resources/vite/",      // No vite setup resources
        "resources/rest/",      // No rest setup resources
        "resources/docker/",    // No docker setup resources
        "Setup\.bx$"            // No setup script
    ];

    return this;
}
```

> **💡 Pro Tip**: Review your `variables.excludes` after running `Setup.bx` to ensure you're not packaging unnecessary setup resources!

### Deploying Your Build:

Once the build completes, you can:

1. **Upload the ZIP**: Deploy `{projectName}-{version}.zip` to your server
2. **Verify Integrity**: Use the checksum files to verify the package wasn't corrupted during transfer
3. **Extract & Run**: Unzip on your server and start with CommandBox

```bash
# On your server
unzip cbtemplate-boxlang-1.1.0.zip
cd cbtemplate-boxlang-1.1.0
box server start
```

> **🚀 Pro Tip**: Integrate `Build.bx` into your CI/CD pipeline to automatically build and deploy your application on every release!

## 📁Application Structure

This ColdBox 8 application follows a clean, modern architecture with the following structure:

### 🏗️ ColdBox Application (`/app/`)

This folder contains the main ColdBox application code via conventions, including configuration files, event handlers, models, views, and more.  This is where you will be coding most of your application logic.

```text
app/
├── 🔧 config/                # Configuration files (Optional)
│   ├── CacheBox.bx           # Caching configuration
│   ├── ColdBox.bx            # Main framework settings
│   ├── Router.bx             # URL routing definitions
│   ├── Scheduler.bx          # Task scheduling
│   └── WireBox.bx            # Dependency injection
├── 🎮 handlers/              # Event handlers (controllers)
├── 🛠️ helpers/               # Application helpers (Optional)
├── 🎨 layouts/               # View layouts
├── 📝 logs/                  # ColdBox logs (Optional)
├── 🏗️ models/                # Business logic models
├── 📦 modules_app/           # Application-specific modules (Optional)
└── 👁️ views/                 # View templates
```

### 🌐 Public Web Root (`/public/`)

This folder contains all the publicly accessible assets and the main application entry point.  The CommandBox or MiniServer or Whatever server will point to this folder as the web root.

```text
public/
├── 📱 Application.bx         # Web-facing application Bootstrap
├── 🎯 index.bxm              # Main entry point (Empty)
├── 🖼️ favicon.ico            # Site icon
├── 🤖 robots.txt             # Search engine directives
└── 📦 includes/              # CSS, JS, images or any resources you want
```

### 🔧 Configuration & Build

This folder contains configuration files, dependencies, Docker setup, and runtime environment.

```text
├── 📋 box.json               # CommandBox dependencies and project descriptor
├── 🏗️ pom.xml                # Maven dependencies (Optional)
├── 🖥️ server.json            # CommandBox Server configuration
├── 🐳 docker/                # Docker configuration (Optional)
├── 🧪 tests/                 # Test suites (NOT OPTIONAL)
├── 📦 modules/               # ColdBox application modules (Managed by CommandBox)
├── ⚙️ runtime/               # BoxLang runtime environment overrides and resources
│   ├── 🔧 boxlang.json               # Custom BoxLang configuration overrides
│   ├── global/               # Global classes and BoxLang components (Optional)
│   │   ├── classes/          # Global BoxLang classes
│   │   └── components/       # Global BoxLang components
│   ├── lib/                  # Runtime libraries (Managed by Maven/CommandBox)
│   ├── logs/                 # BoxLang logs
└── 📚 resources/             # ColdBox/CommandBox module resources
    ├── migrations/           # Database migrations (cbmigrations)
    ├── seeders/              # Database seeders
    ├── swagger/              # API documentation (cbswagger)
    └── other module assets/  # Various module-specific resources
```

## 🗺️ BoxLang Mappings

This template comes pre-configured with essential BoxLang mappings in the `runtime/config/boxlang.json` file to make development seamless. These mappings provide convenient shortcuts to access different parts of your application:

### 📍 Core Application Mappings

```json
"/public": "${user-dir}/public",           // Public web root
"/app": "${user-dir}/app",                 // ColdBox application
"/tests": "${user-dir}/tests",         // Test suites (Can be removed for production)
```

### 🏗️ Framework & Library Mappings

```json
"/coldbox": "${user-dir}/runtime/lib/coldbox",              // ColdBox framework
"/coldbox/system/exceptions": "...coldbox/system/exceptions", // ColdBox exceptions (external)
"/testbox": "${user-dir}/runtime/lib/testbox"               // TestBox testing framework
```

### 📦 Module Mappings

```json
"/modules": "${user-dir}/modules"    // Application modules directory
```

### 🔧 External vs Internal Mappings

- **External mappings** (`"external": true`) - Can be accessed via web requests and file resolution
- **Internal mappings** (`"external": false`) - Only accessible programmatically, not via web requests

This mapping structure ensures your ColdBox application has clean, predictable paths for all its components while maintaining security by controlling web accessibility! 🛡️

## ☕ Java Dependencies

If your project relies on Java third-party dependencies, you can use the included Maven `pom.xml` file in the root. You can add your dependencies there and then run the `mvn install` command to download them into the `runtime/lib` folder. The BoxLang application will automatically class load all the jars in that folder for you! 🎯

You can also use the `mvn clean` command to remove all the jars. 🧹

You can find Java dependencies here: <https://central.sonatype.com/>. Just grab the Maven coordinates and add them to your `pom.xml` file. 📦

## 🐳 Dockerfile

We have included a [`docker/Dockerfile`](docker/Dockerfile) so you can build docker containers from your source code. We have also added two scripts in your `box.json` so you can build the docker image and run the docker image using our [CommandBox Docker](https://hub.docker.com/r/ortussolutions/commandbox) containers.

```bash
# Build a docker **container**
run-script docker:build
# Run the container
run-script docker:run
# Go into the container's bash prompt
run-script docker:bash
```

## 🐙 Docker Compose Stack

We have included a [`docker/docker-compose.yaml`](docker/docker-compose.yml) stack that can be used to run the application in a container alongside a database. We have included support for MySQL, PostgreSQL and MSSQL. We have also included the `run-script docker:stack` command you so you compose the stack up or down.

```bash
run-script docker:stack up
run-script docker:stack down
```

## 💻 VSCode Helpers

We have included two vscode helpers for you:

* `.vscode/settings.json` - Includes introspection helpers for ColdBox and TestBox 🔍
* `.vscode/tasks.json` - Tasks to assist in running a Test Bundle and a CommandBox Task ⚡

We have included two custom tasks:

* `Run CommandBox Task` - Open a CommandBox task and run it 🏃‍♂️
* `Run TestBox Bundle` - Open the bundle you want to test and then run it 🧪

To run the custom tasks open the command palette and choose `Tasks: Run Build Task` or the shortcut `⇧⌘B` 🚀

## 🎉 Welcome to ColdBox

ColdBox *Hierarchical* MVC is the de-facto enterprise-level [HMVC](https://en.wikipedia.org/wiki/Hierarchical_model%E2%80%93view%E2%80%93controller) framework for BoxLang and CFML developers. It's professionally backed, conventions-based, modular, highly extensible, and productive. Getting started with ColdBox is quick and painless. ColdBox takes the pain out of development by giving you a standardized methodology for development with features such as:

* 📐 [Conventions instead of configuration](https://coldbox.ortusbooks.com/getting-started/conventions)
* 🛣️ [Modern URL routing](https://coldbox.ortusbooks.com/the-basics/routing)
* 🚀 [RESTFul APIs](https://coldbox.ortusbooks.com/the-basics/event-handlers/rendering-data)
* 🏗️ [A hierarchical approach to MVC using ColdBox Modules](https://coldbox.ortusbooks.com/hmvc/modules)
* 🎯 [Event-driven programming](https://coldbox.ortusbooks.com/digging-deeper/interceptors)
* ⚡ [Async and Parallel programming constructs](https://coldbox.ortusbooks.com/digging-deeper/promises-async-programming)
* 🧪 [Integration & Unit Testing](https://coldbox.ortusbooks.com/testing/testing-coldbox-applications)
* 💉 [Included dependency injection](https://wirebox.ortusbooks.com)
* 🗄️ [Caching engine and API](https://cachebox.ortusbooks.com)
* 📝 [Logging engine](https://logbox.ortusbooks.com)
* 🌐 [An extensive eco-system](https://forgebox.io)
* 🎊 Much More

## 📚 Learning ColdBox

ColdBox is the defacto standard for building modern BoxLang and ColdFusion (CFML) applications. It has the most extensive [documentation](https://coldbox.ortusbooks.com) of all modern web application frameworks. 📖

If you don't like reading so much, then you can try our video learning platform: [CFCasts (www.cfcasts.com)](https://www.cfcasts.com) 🎥

## 💰 ColdBox Sponsors

ColdBox is a professional open-source project and it is completely funded by the [community](https://patreon.com/ortussolutions) and [Ortus Solutions, Corp](https://www.ortussolutions.com). Ortus Patreons get many benefits like a cfcasts account, a FORGEBOX Pro account and so much more. If you are interested in becoming a sponsor, please visit our patronage page: [https://patreon.com/ortussolutions](https://patreon.com/ortussolutions) ❤️

### 🙏 THE DAILY BREAD

 > "I am the way, and the truth, and the life; no one comes to the Father, but by me (JESUS)" Jn 14:1-12
