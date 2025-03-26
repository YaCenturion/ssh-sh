
# 🚀 GitHub Action: Remote Fetch & Pull  

This GitHub Action allows you to securely executing commands via SSH.

## Features  
- ✅ **Secure SSH connection** using a private key  
- ✅ **Executing commands** You can use in 2 steps  
- ✅ **Easy integration** into any workflow  

## 🛠 Simple example

To use this action in your workflow, add the following to your `.github/workflows/deploy.yml`:  

```yaml
on:
  push:
    branches: [ "deploy" ]
  pull_request:
    branches: [ "deploy" ]
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Executing my commands
        uses: yacenturion/ssh-fetch-pull@v1
        with:
          HOST: "82.10.16.10"
          USERNAME: "root"
          SSH_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
          RUN_MAIN: "whoami; touch nif-naf-nuf.txt"
          RUN_AFTER: "pwd; ls -la"
```

## ⚙️ All Inputs  

| Name        | Description                                                 | Required |
|-------------|-------------------------------------------------------------|----------|
| `HOST`      | Target server hostname or IP address.                       | ✅ Yes    |
| `PORT`      | Target port (default = `22`).                               | ❌ No     |
| `USERNAME`  | SSH username for authentication.                            | ✅ Yes    |
| `SSH_KEY`   | Private SSH key for secure connection (use GitHub Secrets). | ✅ Yes    |
| `RUN_MAIN`  | Bash commands to execute                                    | ❌ No     |
| `RUN_AFTER` | Additional bash commands to execute after                   | ❌ No     |
