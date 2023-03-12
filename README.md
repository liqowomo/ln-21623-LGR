<h1 align="center"><code> 👅:🎂:1w </code></h1>
<h2 align="center"><i><code> curl test --file</code></i></h2>

----
1. [W ?](#w-)
2. [Examples](#examples)
   1. [Special Notes](#special-notes)

----

# W ? 

1. Testing out `curl` download and installs from source 

# Examples 

1. These are the examples 

```sh 
https://getfoundry.sh/
```
- This website asks you to dl using `curl` 

$\Huge Actual \ Code \ pussy$ 

<details>

<summary> 
Script downloaded via the curl command
</summary>

```sh 
#!/usr/bin/env bash
set -e

echo Installing foundryup...

FOUNDRY_DIR=${FOUNDRY_DIR-"$HOME/.foundry"}
FOUNDRY_BIN_DIR="$FOUNDRY_DIR/bin"
FOUNDRY_MAN_DIR="$FOUNDRY_DIR/share/man/man1"

BIN_URL="https://raw.githubusercontent.com/foundry-rs/foundry/master/foundryup/foundryup"
BIN_PATH="$FOUNDRY_BIN_DIR/foundryup"

# Create the .foundry bin directory and foundryup binary if it doesn't exist.
mkdir -p $FOUNDRY_BIN_DIR
curl -# -L $BIN_URL -o $BIN_PATH
chmod +x $BIN_PATH

# Create the man directory for future man files if it doesn't exist.
mkdir -p $FOUNDRY_MAN_DIR

# Store the correct profile file (i.e. .profile for bash or .zshrc for ZSH).
case $SHELL in
*/zsh)
    PROFILE=$HOME/.zshrc
    PREF_SHELL=zsh
    ;;
*/bash)
    PROFILE=$HOME/.bashrc
    PREF_SHELL=bash
    ;;
*/fish)
    PROFILE=$HOME/.config/fish/config.fish
    PREF_SHELL=fish
    ;;
*/ash)
    PROFILE=$HOME/.profile
    PREF_SHELL=ash
    ;;
*)
    echo "foundryup: could not detect shell, manually add ${FOUNDRY_BIN_DIR} to your PATH."
    exit 1
esac

# Only add foundryup if it isn't already in PATH.
if [[ ":$PATH:" != *":${FOUNDRY_BIN_DIR}:"* ]]; then
    # Add the foundryup directory to the path and ensure the old PATH variables remain.
    echo >> $PROFILE && echo "export PATH=\"\$PATH:$FOUNDRY_BIN_DIR\"" >> $PROFILE
fi

# Warn MacOS users that they may need to manually install libusb via Homebrew:
if [[ "$OSTYPE" =~ ^darwin && ! -f /usr/local/opt/libusb/lib/libusb-1.0.0.dylib ]]; then
    echo && echo "warning: libusb not found. You may need to install it manually on MacOS via Homebrew (brew install libusb)."
fi

echo && echo "Detected your preferred shell is ${PREF_SHELL} and added foundryup to PATH. Run 'source ${PROFILE}' or start a new terminal session to use foundryup."
echo "Then, simply run 'foundryup' to install Foundry."

```

</details>

> Location of above file is [`https://github.com/foundry-rs/foundry/blob/master/foundryup/install`](https://github.com/foundry-rs/foundry/blob/master/foundryup/install) - This is the actual curl script



## Special Notes 

1. The above `.sh` file is store as a github gist 