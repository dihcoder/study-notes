## NODE VERSION MANAGER

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash

# List available node versions
nvm ls

# Install an specific node version
nvm install <version-name>
# Example
nvm i lts/hydrogen

# Set the standard node version
nvm alias default <version-name>
```

## RUN COMMANDS FILE

A run command file is a set of instructions for initialization (ex. .bashrc, .vimrc, .npmrc etc)

```bash
echo -e "lts/hydrogen\n" >> .nvmrc
# '-e' is a flag to use characters like the line-break
```
When we run `nvm install`, node will find the file and will install what's inside it.

## DEPENDENCIES

The `package.json` is a Manifest file that lists the project's dependencies

```bash
# To start a node project and create the package.json file, run:
npm init

# To install dependencies, run commands like:
npm i next@13.1.6
npm i react@18.2.0
npm i react-dom@18.2.0
```
