<!-- TODO: Revisit lesson/heading structure to remove need to disable rules -->
<!-- markdownlint-disable MD024 TOP004 -->

### Introduction

Before we start learning, we'll need to install Ruby first. This section is where you could potentially encounter a lot of errors.

Before continuing, let's review a few best practices to keep in mind:

- Copy and paste the commands to avoid typos.
- Follow the directions closely, and don't skip over any sections.
- **Do NOT use `sudo` unless The Odin Project specifically says to do so.** Failing to follow this can cause a lot of headaches, and never run as the `root` user. In some instances, you might see a message in the terminal telling you to use sudo and install something with `apt`. Ignore that and follow *our* instructions for now.

Now, let's get started!

<details markdown="block">

<summary class="dropDown-header">Linux

</summary>

### Step 1: Install updates, packages and libraries

Before we can install Ruby, we need to install some base packages.

#### Step 1.1: Open the terminal

We'll use the terminal to install all of the programs.

If you're using Ubuntu or Xubuntu, press <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>T</kbd> to open the terminal. (This may work in other Linux distributions; you'll have to try!)

**Quick tip:** In Linux, you can copy from the terminal with <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>C</kbd> and paste with <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>V</kbd>.

#### Step 1.2: Update Linux

The rest of the installation will take place inside the terminal window.

First, we need to make sure your Linux distribution is up to date. Run these commands one by one. Because these commands use `sudo`, you will have to enter your password in order for them to run. When typing your password, you may not get any visual feedback, but rest assured that your password is being entered. Once you're done typing your password, press <kbd>Enter</kbd>.

```bash
sudo apt update
sudo apt upgrade
```

When it prompts you, press <kbd>Y</kbd> and then <kbd>Enter</kbd>.

#### Step 1.3: Install packages and libraries

Next, you need to install some required packages that do not come preinstalled. Be sure to copy and paste this command.

```bash
sudo apt install gcc make libssl-dev libreadline-dev zlib1g-dev libsqlite3-dev libyaml-dev
```

When it prompts you, press <kbd>Y</kbd> and then <kbd>Enter</kbd>. You may or may not have to type your password after pressing <kbd>Enter</kbd>.

### Step 2: Install Ruby

Now you're ready to install Ruby. We're going to use a tool called `rbenv`, which makes it easy to install and manage Ruby versions.

#### Step 2.1: Install rbenv

First, you need to clone the rbenv repository.

```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
```

Next command takes care of setting rbenv.

```bash
~/.rbenv/bin/rbenv init
```

Close the terminal window and open a new one to refresh.

Next, you need to install `ruby-build` to help compile the Ruby binaries. Run these commands in the terminal to create a directory for the ruby-build plugin and then download it to the proper directory.

```bash
mkdir -p "$(rbenv root)"/plugins
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
```

Finally, run

```bash
rbenv -v
```

 from your terminal to verify that `rbenv` has been installed correctly. You should get an output with a version number **similar** to this:

```bash
rbenv 1.2.0-14-gc6cc0a1
```

If you do not get a version number at all (anything not starting with `rbenv 1...`), please ask for help in [our Discord server](https://discordapp.com/channels/505093832157691914/505093832157691916).

#### Step 2.2: Install Ruby

It's finally time to install Ruby using `rbenv`!

Inside the terminal, run this command:

```bash
rbenv install 3.3.5 --verbose
```

This command will take 10-15 minutes to complete. The `--verbose` flag will show you what's going on so you can be sure it hasn't gotten stuck. While it installs, take this time to watch [funny jumping goats video](https://youtu.be/X2CYWg9-2N0) or to get a glass of water.

You may get this error message:

```bash
ruby-build: definition not found: x.x.x

See all available versions with `rbenv install --list'.

If the version you need is missing, try upgrading ruby-build:

  git -C /home/itorja/.rbenv/plugins/ruby-build pull
```

If so, we run the suggested command:

```bash
git -C "$(rbenv root)"/plugins/ruby-build pull
```

Once Ruby is installed, you need to tell rbenv which version to use by default. Inside the terminal, type:

```bash
rbenv global 3.3.5
```

Then,

```bash
ruby -v
```

The above command should return something similar to this:

```bash
ruby 3.3.5pxx (20xx-xx-xx revision xxxxx) [x86_64-linux]
```

where x represents the version available at the time you installed Ruby.

Well done! Pat yourself on the back! The hard part is done, and it's time to move on to the next lesson!

</details>

<details markdown="block">

<summary class="dropDown-header">MacOS

</summary>

### Step 1: Install packages and libraries

Before we can install Ruby, we need to install some base packages. We will use the terminal to install all of the programs.

#### Step 1.1: Open the terminal

In your Applications folder, find "Utilities" and double click "Terminal". Alternatively, using Spotlight (<kbd>Cmd</kbd> + <kbd>Space</kbd>) or Launchpad, type "Terminal".

The rest of the instructions are done inside this terminal window and if you followed all the Foundations instructions, you should have already completed step 1.2 and 1.3.

#### Step 1.2: Install Xcode

First, you need to install Xcode, which is a program provided by Apple for programming. Xcode will install many programs that are needed for Ruby and Git and should take 10-15 minutes to install.

Type `xcode-select --install` in your terminal and press <kbd>Enter</kbd>. You may need to click "Install" when prompted.

#### Step 1.3: Install Homebrew

The next program you need to install is [Homebrew](https://brew.sh/), which makes it easy to install other programs you'll need. From inside the terminal, type the following:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

You will be prompted to enter your password. When typing your password, you may not get any visual feedback, but rest assured that your password is being entered. Once you're done typing your password, press <kbd>Enter</kbd>.

To verify the Homebrew installation, we can run

```bash
which brew
```

If it outputs a certain path, you're good to go ahead! But if the terminal reads ```brew not found```, please go through the [MacOS instructions in the setting up git lesson](https://www.theodinproject.com/lessons/foundations-setting-up-git) to get homebrew installed.

Congratulations! You've installed the prerequisites!

### Step 2: Install Ruby

Now you're ready to install Ruby. We're going to use a tool called `rbenv`, which makes it easy to manage Ruby versions.

#### Step 2.1: Install ruby-build

First, let's install `ruby-build`:

```bash
brew install ruby-build
```

`ruby-build` will make it possible to install our Ruby version of choice.

#### Step 2.2: Install rbenv

To install `rbenv`, run the following in your terminal:

```bash
brew install rbenv
```

Then, run this command:

```bash
rbenv init
```

At this point, open a new terminal tab, so changes take effect.

To confirm that everything went as it should, open a new terminal tab and run:

```bash
rbenv -v
```

You should get an output with a version number **similar** to this:

```bash
rbenv 1.2.0-14-gc6cc0a1
```

If you do not get a version number at all (anything not starting with `rbenv 1...`), please ask for help in [our Discord server](https://discordapp.com/channels/505093832157691914/505093832157691916).

#### Step 2.3: Install Ruby

We can now (finally) install Ruby! Our curriculum currently uses version 3.3.5, which will allow you to complete this path's materials and content without error. We upgrade the material to accommodate newer versions as necessary. Without further ado, let's get going!

First, let's upgrade `ruby-build`:

```bash
brew upgrade ruby-build
```

Now we're ready to install our desired version of Ruby:

```bash
rbenv install 3.3.5 --verbose
```

This command will take 10-15 minutes to complete. The `--verbose` flag will show you what's going on so you can be sure it hasn't gotten stuck. While it installs, take this time to watch [funny jumping goats video](https://www.youtube.com/watch?v=X2CYWg9-2N0) or to get a glass of water.

Once Ruby is installed, you need to tell rbenv which version to use by default. Inside the terminal, type:

```bash
rbenv global 3.3.5
```

You can double check that this worked by typing `ruby -v` and checking that the output says version 3.3.5:

```bash
ruby -v
```

You should get an output with a version number **similar** to this:

```bash
ruby 3.3.5pxx (20xx-xx-xx revision xxxxx) [x86_64-darwin18]
```

If you don't see the output above, close and reopen the terminal window and then run the command again.

Well done! Pat yourself on the back! The hard part is done, and it's time to move on to the next lesson!

</details>

#### Extras

If you are using Visual Studio Code as your IDE, you can install the "Ruby LSP" extension, which will provide you with semantic highlighting and formatting support.

Using the extension is optional, but it is a quick install; go to the "Extensions" tab in VSC (<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>X</kbd>), search "Ruby LSP", and click install on the first one. Congratulations, the extension is now installed.

The most important features Ruby LSP provides will work out of the box. But it may bug you about using a monorepo setup, missing lockfiles or rubocop - you can choose "Don't show again" for now. We will introduce these later.
