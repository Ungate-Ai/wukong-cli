# wukong-cli-releases
Wukong-Cli is our entrypoint for the trust layer for AI Agents

## Quick Start

## Install Wukong CLI
### Linux/MacOS:
Open the Terminal 
- Go to the directory where the binary is downloaded
```
bash install.sh
```
This will ask for your machine's/user's password (needs sudo permission)
### Windows:
Open the Command Prompt
```
install.bat 
```
(or right click and run as administrator)

### Login to Wukong

```bash
wukong login
```
You will be asked for a 
- wallet name: For easy identification
- private key of the wallet

This should be an ERC20 wallet. Deposit 0.001 ETH and 1 USDC to the wallet on the Arbitrum One network.
  
### Create a deployment

```bash
wukong deployment create
```


Commands
Global Flags
user-address - Set the default user address to be used for the current command execution. It overrides the default user.
wukong deployment get --user-address="wallet_address"
User
Login
Authenticate with your wallet credentials. Supports both interactive and non-interactive modes.

```bash
wukong login
```

```bash
wukong login --non-interactive --name "my-wallet" --private-key "your-private-key"
```

```bash
wukong login --name "my-wallet"
```
Flags:

--name: Name for the wallet
--private-key: Your wallet's private key
--non-interactive: Disable interactive prompts (requires all necessary flags)
Logout
Logout the current user. You can set the specific user wallet address to logout using the global --user-address flag.

# Mixed mode
```bash
wukong logout --set-default="0x{wallet_address}"
```
Flags:

--set-default: Set the default wallet address that has already logged in, in case the default user is being currently logged out.
Set Default Profile
Set the default user profile that is used to perform operations.

# All Modes
```bash
wukong user set-default [wallet-address]
```

### Display User profile
Displays the user profile for the current user.

# All Modes
```bash
wukong user display
```

### Deployments
Create Deployment
Deploy a project from a GitHub repository.

# Interactive mode
```bash
wukong deployment create
```

# Non-interactive mode
```bash
wukong deployment create --non-interactive --wallet-private-key="<wallet_pvt_key>" --github-url "https://github.com/user/repo" --github-branch "main" --env-path "./config/.env" --character-file-path="./character.json" --duration="15"
```

# Mixed mode
```bash
wukong deployment create --github-url "https://github.com/user/repo"
```
Flags:

--github-url: GitHub repository URL
--github-branch: GitHub Branch from where the code is to be fetched.
--env-path: Path to environment file. It must be in a .env format
--character-file-path: Path to character file. It must be in JSON format
--wallet-private-key: The private wallet key of the user.
--duration: The duration for the deployment in minutes.
--non-interactive: Disable interactive prompts (requires all necessary flags)
List Deployments
View all your current deployments with flexible output formats.

# Default table output
```bash
wukong deployment get
```

# JSON output
```bash
wukong deployment get --output json
```
Flags:

--output: Output format (table, json)
Get Specific Deployment
View details of a specific deployment.

# Using argument (legacy mode)
```bash
wukong deployment get <job-id>
```

# Using flag
```bash
wukong deployment get --id <job-id>
```

# With JSON output
```bash
wukong deployment get --id <job-id> --output json
```
Flags:

--id: Deployment ID to fetch
--output: Output format (table, json)
Configuration
Wukong stores user session in your home directory:

~/.wukong/default.json
Security
Wukong uses secure wallet-based authentication
Private keys are never stored locally
All communications with servers are encrypted
Session tokens are stored securely
Examples
Interactive Deployment
# Login interactively
wukong login 

# Create a deployment with prompts
```bash 
wukong deployment create
```

# Check deployment status
```bash
wukong deployment get
```

### Non-Interactive Deployment
# Login non-interactively
```bash
wukong login --non-interactive --name "prod-wallet" --private-key "your-private-key"
```

# Create deployment without prompts
```bash
wukong deployment create --non-interactive --github-url "https://github.com/user/repo" --env-path "./config/.env"
```

# Check deployment status in JSON format
```bash
wukong deployment get --output json
```

## Troubleshooting

### Common Issues
Login Failed

Verify your wallet name and private key
Check if all required flags are provided in non-interactive mode
Ensure you have an active internet connection
Deployment Failed

Check if the GitHub repository URL is correct
Verify the environment file path is valid
Ensure all required flags are provided in non-interactive mode
Verify all required files are present in the repository
Command Not Found

Ensure Wukong CLI is properly installed
Check if the installation directory is in your PATH

