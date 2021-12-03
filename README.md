# Getting Started

# From Complete Scratch
From a brand new system
## Install Node 
There are several ways to get and install node.js but
nvm is the recommended way. It can be installed using the
installer script:

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```
This will install into `~/.nvm` and attempt to update your profile.
For more info or trouble shooting please visit the github page for nvm
at https://github.com/nvm-sh/nvm.

Once you have nvm you can install the latest node version
```
nvm install node
```

all of this is to get yarn. Corepack within node is the perfered
way to manage yarn. With Node >= 16.10 you can enable corepack
with `corepack enable`. Node < 16.10 you will need to run 
`npm i -g corepack`

## Install Rust
Install Rustup with ```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Configure your shell
```
source $HOME/.cargo/env
```
Add the wasm target to you toolchin
```
rustup target add wasm32-unknown-unknown
```
If you have any issues take a look at the rust install page https://www.rust-lang.org/tools/install

## Install the near-cli
After all of that we can finally install the near CLI
```
npm install near-cli -g
```

This is our entry to creating accounts, deploying contracts,
and intereacting with the near blockchain.

## Creating a new project
This method is currently being reworked for something better
but for the time being there exists a command on mpx to create
a near app.
```
npx create-near-app <project directory> --frontend <vanilla|react> --backend <assemblyscript|rust>
```
If no frontend or backend arguments are set a vanilla frontend and
assemblyscript backend will be created.

Yarn will run, fetch all of the required packages and autogenerate
all files that are needed to run.

Please check out the pckage.json to see helpful commands under the
scripts section. `yarn prestart && yarn dev` will deploy the application
to the testnet using a dev account autoloaded with 200 near. This is
very useful and an ideal way to ensure your application is working
as desired.

source the neardev env file `source neardev/dev-account.env` this will
export the account name for the contract to `$CONTRACT_NAME`

## Optional Login / Create non dev test account
You will either need to create a new account or import your keys with the[NEAR Wallet](https://wallet.testnet.near.org).

In the project root, login with `near-cli` by following the instructions after this command:

```
near login
```

It becomes helpful if you export your account as ID `export ID=<your account id>`

## Wrapping up
When you are done with your test account you can transfer the remaining
balance to your main test account with the cli.

```
near delete $CONTRACT_NAME $ID
```

# Useful links
https://docs.near.org/docs/develop/basics/getting-started
