# TorchServer

VSCode project to easily set up, configure and navigate configurations of a Torch server.

## Installing VSCode

Open powershell in adminstrator mode & type the following commands:

```powershell
set-executionpolicy remotesigned
```

```powershell
winget install --id Microsoft.VisualStudioCode -e -h --accept-package-agreements
```

```powershell
code --install-extension ms-vscode.PowerShell
```

```powershell
code .
```

## Installing Torch

On VSCode, open the terminal window by keymap `` Ctrl + Shift + ` `` or the tab menu `Terminal > New Terminal`.

Type in the following command in the VSCode terminal:

```powershell
. './Scripts/DownloadTorch.ps1'
```

Press `F5` key to launch the Torch server. Launcher will then download the SE dedi server files for you. This may take some minutes. 

Upon Torch server's GUI startup, you'll see the following warning in the log:
> 03:36:14.1209 [WARN]   InstanceManager: No worlds found in the current instance C:\torch-server\Instance.

Close the Torch server app.

## Setting Up Game World

Under `Content/CustomWorlds`, find the world that you want to start with; let's say `Star System`.
Then type the following command in the VSCode terminal:

```powershell
. ./Scripts/CopyWorld.ps1 "Star System"
```

Now, `Star System` is copied over to the instance folder, and ready to serve players.

**TODO: Support multiple world saves.**

## Configure Torch

Start up Torch by pressing `F5` and apply your configuration on GUI.

## Auto Restart

To recover from silent crashes, edit `.vscode/launch.json` as follows:

```diff
- "script": "./Torch.Server.exe",
+ "script": "./Scripts/AutoRestart.ps1",
```

## Helper Scripts

Project comes with scripts useful for admin work.

### Renaming the world
World name is supposed to be configured in multiple files and this script will do that for you.
```powershell
. ./Scripts/RenameWorld.ps1 Foo
```
#### Fixing installation path
Installation path is supposed to be configured in multiple files and this script willd do that for you.
```powershell
. ./Scripts/FixPath.ps1
```

Find more scripts in `/Scripts`.
