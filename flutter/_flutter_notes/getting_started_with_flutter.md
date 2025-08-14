# Getting Started with Flutter

This guide walks you through setting up a complete Flutter development environment, creating your first project, and establishing a version control workflow with Git and GitHub. It is designed for beginners to build a clean and efficient foundation for developing Flutter applications.

## Step 1: Install Visual Studio Code

Visual Studio Code (VS Code) is a lightweight yet powerful [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment) recommended for Flutter development due to its minimalistic design, speed and excellent Dart and Flutter support.

1. Download and install the latest version for your operating system from the [official VS Code website](https://code.visualstudio.com/download).
2. Install the following essential extensions from the VS Code Marketplace:
   - **Dart** ([`Dart-Code.dart-code`](https://marketplace.visualstudio.com/items?itemName=Dart-Code.dart-code)): Provides core Dart language support, including syntax highlighting, code completion, and analysis.
   - **Flutter** ([`Dart-Code.flutter`](https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter)): Adds Flutter-specific features like hot reload, widget inspection, and device management.

> **Tip:** Check out the [offical VS Code docs](https://code.visualstudio.com/docs).

## Step 2: Install Android Studio

While VS Code will be our primary editor, installing Android Studio is highly recommended. It provides the full [Android SDK](https://en.wikipedia.org/wiki/Android_SDK), build tools, and [emulator](https://en.wikipedia.org/wiki/Emulator) for testing your mobile apps on Android.

Download and install Android Studio from the [official Android Developer website](https://developer.android.com/studio).

## Step 3: Install the Flutter SDK

Flutter is a [cross-platform](https://en.wikipedia.org/wiki/Cross-platform_software) UI [framework](https://en.wikipedia.org/wiki/Software_framework) for building natively compiled applications for mobile, web, and desktop from a single codebase.

1. Visit the [official Flutter documentation](https://docs.flutter.dev/get-started/install) and follow the platform-specific instructions to download and install the Flutter SDK.
2. Add the `flutter/bin` directory to your system’s `PATH` environment variable to access the `flutter` command from any terminal. See the [official guide to updating your path](https://docs.flutter.dev/get-started/install/post-install-add-to-path).
3. Verify the installation and check for missing dependencies by running:
   ```sh
   flutter doctor
   ```
   Follow any instructions provided by `flutter doctor` to resolve issues.
4. Finally, verify the version:
   ```sh
   flutter --version
   ```

## Step 4: Keep the Flutter SDK Updated

Flutter is actively developed. Regularly updating the SDK ensures you have the latest features, performance improvements, and bug fixes.

1. Run the following command in your terminal to upgrade to the latest stable version:
   ```sh
   flutter upgrade
   ```
2. Verify the installed version again to confirm the update:
   ```sh
   flutter --version
   ```

> **Tip**: Run `flutter upgrade` periodically (e.g., weekly) to stay current. You can check the latest stable version on the [Flutter SDK archive page](https://docs.flutter.dev/development/tools/sdk/releases).

## Step 5: Install and Configure Git

[Git](https://en.wikipedia.org/wiki/Git) is the industry-standard version control system for tracking code changes. [GitHub](https://en.wikipedia.org/wiki/GitHub) is a platform for hosting your Git repositories online.

### Install Git

- **Windows**: Download and install from [git-scm.com/download/win](https://git-scm.com/download/win).
- **macOS**: Install Homebrew from the [official website](https://docs.brew.sh/Installation), then run `brew install git`. Alternatively, download from [git-scm.com/download/mac](https://git-scm.com/download/mac).

### Verify Git Installation

Open your terminal and run:

```sh
git --version
```

### Configure Git

Set your name and email, which will be attached to your commits:

```sh
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Set Up GitHub Authentication

1. Create a free account at [github.com](https://github.com) if you don’t have one.
2. Generate a Personal Access Token (PAT):
   - Go to **Settings > Developer settings > Personal access tokens > Tokens (classic)**.
   - Click **Generate new token (classic)**, name it (e.g., "Flutter Project"), select the `repo` scope, and copy the token securely.
3. Use HTTPS for repositories and the PAT as your password when prompted.
4. Optionally, cache credentials:
   ```sh
   git config --global credential.helper cache
   ```

> **Tip:** Check out the [offical GitHub docs](https://docs.github.com/).

## Step 6: Create a New Flutter Project

Project names should be descriptive, lowercase, and use underscores instead of spaces (e.g., `todo_list_app`).

> **Important**: Never create projects inside a folder synced with cloud services like Google Drive, iCloud, or OneDrive. This can cause file locking issues, build failures, and security risks. Always use a dedicated local folder for your source code and rely on Git/GitHub for cloud backup and versioning.

1. **Create the Project**:
   - For a project supporting **all platforms** (mobile, web, desktop):
     ```sh
     flutter create todo_list_app
     ```
   - To create a **web-only** project:
     ```sh
     flutter create todo_list_app --platforms web
     ```
2. **Navigate into your new project directory**:
   ```sh
   cd todo_list_app
   ```

## Step 7: Initialize Git and Push to GitHub

1. **Initialize a Local Git Repository**:

   ```sh
   git init -b main
   git add .
   git commit -m "Initial commit: Create Flutter project"
   ```

   > The `-b main` flag sets the default branch name to `main`, which is the modern standard.

2. **Create a Remote Repository on GitHub**:

   - Go to [github.com](https://github.com) and click **New repository**.
   - Name your repository (e.g., `todo_list_app`).
   - Choose **Private** unless you intend for the code to be public.
   - **Important**: Do not initialize the repository with a README, license, or `.gitignore` file, as your local project already has these.

3. **Link the Local and Remote Repositories and Push**:
   ```sh
   git remote add origin https://github.com/your-username/todo_list_app.git
   git push -u origin main
   ```
   When prompted, enter your GitHub username and PAT as the password.

> **Note**: Replace `your-username` with your actual GitHub username.

## Step 8: Understand the `.gitignore` File

The `flutter create` command automatically generates a `.gitignore` file. This file tells Git to ignore files and folders that shouldn't be tracked in version control, such as:

- IDE-specific configuration files (`.idea/`, `.vscode/`).
- Build artifacts (`build/`).
- Secret files and local configuration (`.env`).
- Generated Dart files.

This keeps your repository clean and focused only on your source code. You should not delete this file or the files it ignores.

## Step 9: Configure `pubspec.yaml`

The `pubspec.yaml` file is the heart of your project’s configuration. It defines metadata, dependencies (packages), and settings.

Update it with your project’s details. Here is a sample configuration:

```yaml
name: todo_list_app # Must match your project folder name
description: A beautifully designed TODO list app # Provide a concise description
publish_to: none
version: 1.0.0+1

environment:
  sdk: ">=3.3.3 <4.0.0"

dependencies:
  flutter:
    sdk: flutter
  cupertino_icons: ^1.0.8

dev_dependencies:
  flutter_test:
    sdk: flutter
  flutter_lints: ^4.0.0 # Enables linting based on analysis_options.yaml

flutter:
  uses-material-design: true
```

> **Note**: Ensure the `name` field matches your project folder name exactly. After updating, run `flutter pub get` to install dependencies.

## Step 10: Set Up the `analysis_options.yaml` File

The `analysis_options.yaml` file enforces code quality and formatting rules. Use this configuration:

```yaml
include: package:flutter_lints/flutter.yaml
# You can add custom rules here later.
linter:
  rules:
    - prefer_const_constructors
```

## Step 11: Configure Web-Specific Settings

For web apps, update metadata in the `web/` directory.

1. **Update `web/manifest.json`**:

   ```json
   {
     "name": "TODO List App",
     "short_name": "TODO App",
     "description": "A beautifully designed TODO list app for managing tasks",
     ...
   }
   ```

2. **Update `web/index.html`**:
   ```html
   <meta
     name="description"
     content="A beautifully designed TODO list app for managing tasks"
   />
   <title>TODO List App</title>
   ```

## Step 12: Run Your Application

1. Open the project in VS Code:
   ```sh
   code .
   ```
2. Select a device in the bottom-right status bar (e.g., Chrome for web).
3. Press F5 or **Run > Start Debugging** to launch with hot reload.

Alternatively, run from terminal:

```sh
flutter run
```

## Step 13: Basic Android & iOS Setup (Coming Soon)

Placeholders for platform-specific setup like app icons, splash screens, and permissions.

## Additional Best Practices

- **Version Control Workflow**: Commit changes frequently with descriptive messages:
  ```sh
  git add .
  git commit -m "feat: Add user login screen"
  git push
  ```
- **Secrets Management**: Never commit API keys or passwords. Use a `.env` file (ignored by `.gitignore`) with `flutter_dotenv`.
- **Next Steps**: Explore the official [Flutter Documentation](https://docs.flutter.dev) for widgets, state management, and UI building.
