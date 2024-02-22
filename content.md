# Install Ruby Locally

## Install VSCode

Install **[VS Code](https://code.visualstudio.com/Download)**.

### `code` command

In the context of Visual Studio Code (VSCode), the **`code`** command in the **`PATH`** refers to a command-line interface tool provided by VSCode that allows you to open files and folders directly from the command line.

When you install VSCode, it typically offers the option to add itself to the system's **`PATH`** environment variable during installation. Adding VSCode to the **`PATH`** enables you to open VSCode from any directory in your command line or terminal without needing to provide the full path to the VSCode executable.

To install the `code` command, type Cmd+Shift+P and start typing `install code` and select "Install 'code' command in PATH". This will add the **`code`** command to your shell so you can open up VS Code from your terminal.

```bash
# Examples
code myfile.txt # open a specific file
code myfolder # open a specific folder
```

## What is Homebrew?

Homebrew is a package manager for macOS (and Linux) that simplifies the process of installing, updating, and managing software packages and libraries. It's like an app store for your command line. Here's what it does:

1. **Package Installation**: Homebrew allows users to easily install software packages and libraries from the command line. Instead of searching for installation files or downloading from websites manually, Homebrew handles everything for you.
2. **Dependency Management**: Many software packages rely on other libraries or tools to function properly. Homebrew automatically manages these dependencies, ensuring that everything required for a package to work is installed correctly.
3. **Updates**: Homebrew simplifies the process of keeping software up to date. Users can easily update all installed packages with a single command, ensuring that they have the latest features and security patches.
4. **Version Control**: Homebrew allows users to install specific versions of software packages if needed. This can be useful for compatibility reasons or if a user prefers an older version for some reason.
5. **Configuration Management**: Homebrew provides options for configuring how packages are installed and managed, giving users flexibility and control over their software environment.

Overall, Homebrew streamlines the process of managing software on macOS, making it easier for users to install, update, and maintain the tools they need for development and everyday use.

### Install Homebrew

In the terminal run this command:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After the initial install you will be instructed to run 2 commands in your terminal. Please copy the specific commands from your terminal as they are specific to your system

```bash
# Example (please use the commands listed in your terminal)
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/dpi-pttl-3/.zprofile

eval "$(/opt/homebrew/bin/brew shellenv)"
```

## What is rbenv

`rbenv` is a tool used in Ruby development to manage different versions of the Ruby programming language on a single machine. Here's what it does:

1. **Version Management**: `rbenv` allows developers to install and switch between multiple versions of Ruby on their system. This is particularly useful when working on projects that require different versions of Ruby due to compatibility or dependency reasons.
2. **Isolation**: `rbenv` provides a way to isolate different Ruby environments for different projects. Each project can have its own Ruby version specified, ensuring that dependencies and configurations do not conflict between projects.
3. **Integration with Shell**: `rbenv` integrates with the shell environment, allowing users to set a specific Ruby version globally or per project using simple commands. This ensures that the correct Ruby version is used when running Ruby scripts or applications.
4. **Plugin System**: `rbenv` has a plugin system that extends its functionality. Users can install plugins to add features such as automatic switching of Ruby versions based on the directory or environment variables.

Overall, `rbenv` simplifies the process of managing Ruby versions and environments, making it easier for developers to work on multiple projects with different Ruby requirements without conflicts.

### Install rbenv

Link to github repo: https://github.com/rbenv/rbenv

In the terminal run this command:

```bash
brew install rbenv ruby-build
```

Load rbenv in your shell

```bash
# run this and follow the printed instructions:
rbenv init
```

To automatically load rbenv please append this code to your ~/.zshrc file

```bash
# Open ~/.zshrc in VSCode by typing this into the terminal
code ~/.zshrc

#Paste this code in your file, save the file and close it
eval "$(rbenv init - zsh)"
```

Close your terminal and launch a new one for changes to take effect

### Choose a version of Ruby to install

```bash
# install a Ruby version:
rbenv install 3.2.1
```

Once the install is complete close your terminal and launch a new one for changes to take effect

### Set a Ruby version

```bash
rbenv global 3.1.2   # set the default Ruby version for this machine
# or:
rbenv local 3.1.2    # set the Ruby version for this directory
```

### Check and see if Ruby was updated

```bash
ruby -v
# should show the newly installed version of Ruby
# => 3.2.1
```

### rbenv commands for future reference

```bash
Some useful rbenv commands are:
   commands    List all available rbenv commands
   local       Set or show the local application-specific Ruby version
   global      Set or show the global Ruby version
   shell       Set or show the shell-specific Ruby version
   install     Install a Ruby version using ruby-build
   uninstall   Uninstall a specific Ruby version
   rehash      Rehash rbenv shims (run this after installing executables)
   version     Show the current Ruby version and its origin
   versions    List installed Ruby versions
   which       Display the full path to an executable
   whence      List all Ruby versions that contain the given executable
```

## Install Rails

Installing Rails is as simple as running the following command in your Terminal:

```bash
gem install rails -v 7.1.3
```

Once the install is complete close your terminal and launch a new one for changes to take effect

And now we can verify Rails is installed:

```bash
rails -v
# Rails 7.1.3
```

## Install PostgreSQL

You can install **[PostgreSQL](http://www.postgresql.org/)** server and client from Homebrew:

```bash
brew install postgresql
```

Once this command is finished, it gives you a couple commands to run. Follow the instructions and run them:

```bash
# To have launchd start postgresql at login:
brew services start postgresql
```

By default the postgresql user is your current macOS username with no password. For example, my macOS user is named `pttl-42` so I can login to postgresql with that username.

```bash
psql pttl-42
```

## Configuring git

We'll be using Git for our version control system so we're going to set it up to match our **[Github](https://github.com/)** account. If you don't already have a Github account, make sure to **[register](https://github.com/)**. It will come in handy for the future.

Replace the example name and email address in the following steps with the ones you used for your Github account.

```bash
git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
ssh-keygen -t ed25519 -C "YOUR@EMAIL.com"
```

The next step is to take the newly generated SSH key and add it to your Github account. You want to copy and paste the output of the following command and **[paste it here](https://github.com/settings/ssh)**.

```bash
cat ~/.ssh/id_ed25519.pub
```

Once you've done this, you can check and see if it worked:

```bash
ssh -T git@github.com
```

You should get a message like this:

```bash
Hi {github username}! You've successfully authenticated, but GitHub does not provide shell access.
```
