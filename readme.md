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

## 📁 Application Structure

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
