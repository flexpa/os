# 🍺 Homebrew

[Homebrew](https://brew.sh/) (or `brew`) is a package manager for macOS. You can use Homebrew to manage the install of most of the [.](./ "mention").

### Setup

From a completely fresh Macbook, you'll need to first configure the local git installation. If you don't do this, you can't finish installing `brew`.

```bash
git config --global user.email you@flexpa.com
```

Install `brew` with the instructions at this link:

{% embed url="https://brew.sh" %}
brew.sh has the install instructions
{% endembed %}

### Install everything from [.](./ "mention")

To show off the power of `brew`, install all of our team tools at once:

```sh
brew install --cask 1password
brew install --cask 1password-cli
brew install --cask slack
brew install --cask loom
brew install --cask around
brew install --cask visual-studio-code
brew install --cask gpg-suite
brew install jq
```

#### Extras

```sh
brew install --cask cron
```

### 1Password CLI Config Setup

1\. Install [1password-cli](https://developer.1password.com/docs/cli/get-started) with homebrew above

2\. `op account add --address flexpa.1password.com --email you@flexpa.com`

3\. Enter your secret key (you can find that on [https://flexpa.1password.com/profile](https://flexpa.1password.com/profile))

4\. Run `eval $(op signin flexpa)`

5\. Be sure to have installed jq, a command-line JSON processor.

### Updating

```sh
brew upgrade
```

### Visual Studio Code Live Share

VS Code Live Share is an extension that gives us the opportunity to simultaneously write and review code on VS Code.&#x20;

Before downloading this extension, you must install Rosetta 2, which enables a Mac with Apple silicon to use apps built for a Mac with an Intel processor.&#x20;

To install Rosetta, enter the following in your terminal:

```bash
softwareupdate --install-rosetta
```

Once installed, restart your computer.

Now you can easily install Live Share from Extensions in VS Code. Further instructions and information on Live Share can be found [here](https://code.visualstudio.com/learn/collaboration/live-share).
