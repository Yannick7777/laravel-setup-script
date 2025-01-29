## Setup
### Windows with VSCode
- If wsl isn't installed yet install it by executing `wsl --install` in your preferred shell
- Open WSL from startmenu or your preferred shell by executing `wsl`
- Open vscode by executing `code`
- Wait until the VSCode server is installed
- VSCode should open up. Press F1 and use `WSL: Connect to WSL` command
- Press F1 and use `Git: Clone` to clone this repo
- Press F1 and use `Git: Clone` again. Make sure to clone it into this repo's folder and to NOT open the cloned repository and instead click `cancel`
- Rename your project to `laravel` by either using the `mv` command in the VSCode terminal or by right-clicking on the directory in VSCode and clicking `rename`
- Start Docker Desktop on Windows
- Type `./setup` into the VSCode terminal
- Type `./start` into the VSCode terminal
- Done!
#### Tips & Tricks
- If you encounter any Docker related issues, it might to close Docker Engine and stop wsl by executing `wsl -t ubuntu` in your preferred shell. After that, start both again
- If you want to commit to your laravel repo with the VSCode F1 commands, make sure to switch the folder you're in to your repo first. This can be done via `File` => `Open Folder...`