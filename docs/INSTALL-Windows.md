# Installing OCaml for Windows systems

Brief instructions on setting up a modern OCaml development environment on Windows

## Prerequisites

1. If you already use a dual-boot setup to run both Windows and Linux distribution (Ubuntu, Arch, and friends), then its recommended to not use Windows and switch to Linux for the tutorial. If not, continue reading.
1. If you're using the GitHub Codespaces method described below, you can skip the remaining prerequisites.
1. An up-to-date recent modern version of Windows 10 or 11 which already has the following:
    - WinGet - Easily install and manage applications, Refer: https://learn.microsoft.com/en-us/windows/package-manager/winget/
    - Powershell 7+ - Available via WinGet, Refer: https://learn.microsoft.com/en-us/powershell/scripting/install/install-powershell-on-windows?view=powershell-7.6#install-powershell-using-winget-recommended
    - WSL2 (Optional)
1. This tutorial mainly uses Visual Studio Code (VSCode). If you're using a different editor, some instructions may be different. Download VS Code from https://code.visualstudio.com/

We'll be using VSCode along with its plugins for OCaml & Docker Containers to provide a seamless experience of OCaml on Windows

## Installation

To ensure a working OCaml workshop setup for Windows, there are multiple options:

1. GitHub Codespaces (Fastest)
1. Local Setup: using VSCode Dev Containers (Preferred)
1. Local Setup: manually, using Powershell

### (Fastest) GitHub Codespaces

Run the exercises directly in your browser! View this project on GitHub with GitHub Codespaces (uses the provided devcontainer setup). 

1. If not already, open your preferred browser & login to GitHub. From there, open the workshop link: https://github.com/fplaunchpad/learn-ocaml-workshop-2026
1. Click on "Code" menu. 
1. Select “Create codespace on main” from the “Codespaces” tab in the “Code” menu. 
1. This will take a few minutes to finish (You'll see a progress bar at the bottom right). Once its done, you'll have a working editor right in your browser and can work on OCaml directly.
1. Head over to 'Start using your setup' section.

### (Preferred) Local setup: using Dev Containers

Please note that the following steps may take less than half an hour to more than a few hours depending on your system and internet setup.

1. On a system with VS Code, install the following extensions:
    - OCaml Platform extension; available here: https://marketplace.visualstudio.com/items?itemName=ocamllabs.ocaml-platform
    - Dev Containers extension; https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers

1. On Windows 10 Pro/Enterprise, follow the instructions to install Docker Desktop (2.0 or above) to be used by the Dev Containers Extension. Refer https://code.visualstudio.com/docs/devcontainers/tutorial

Alternatively, in case the above doesn't work, you can try using WSL2 and the WSL extension for VS Code. 
WSL Installation can be done using Powershell (in administrator mode) as described here https://learn.microsoft.com/en-us/windows/wsl/install
Install the WSL Extension for VS Code from https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl
Make sure to reference the troubleshooting steps in the visual studio [containers page](https://code.visualstudio.com/remote/advancedcontainers/docker-options#_windows-windows-subsystem-for-linux-wsl) or [docker page](https://docs.docker.com/desktop/features/wsl/).

1. Now you are ready to start using the workshop contents. The tutorial contents can be accessed at the following URL: https://github.com/fplaunchpad/learn-ocaml-workshop-2026 

1. Open a new Window on VS Code and use the Clone Git Repository and paste the above url.

While Git/GitHub isn't a prequisite, please feel free to refer to Step 1 Option A of VS Code Quickstart docs: https://code.visualstudio.com/docs/sourcecontrol/quickstart#_step-1-open-a-project (or this [blogpost](https://www.jcchouinard.com/git-clone-github-repository-vscode/) )

1. To successfully open and edit files you may need to click on Trust Authors to continue tinkering with the codebase.

1. If you have the Dev Containers extension installed, you'll see a Popup (usually at Lower Right Portion) allowing you to reload the folder in a Dev Container. Click on 'Reopen in Container' (or go to Command Palette (Ctrl+Shift+P) and type "Dev Containers: Reopen in Container"). 

1. Now VSCode will install the necessary requirements to setup a ready-to-use working install of OCaml in a local Docker Container! (this might take a while)

### Alternative Local setup: manual method

1. Open Powershell. Using WinGet install the following

```sh
winget install Git.git OCaml.opam
```

1. Setup opam - OCaml's package manager

```sh
opam init --yes --bare && \
    opam update -a && \
    opam switch create default 5.4.0 --yes
# restart powershell once its done
(& opam env --switch=default) -split '\\r?\\n' | ForEach-Object { Invoke-Expression $_ }
```

1. Install necessary dependencies we'll be using

```sh
opam install ocaml-lsp-server odoc ocamlformat utop async core js_of_ocaml js_of_ocaml-ppx merlin ocp-indent
opam install ocaml.5.4.0
```

## Start using your Setup

Once you have a working setup using any of the above steps, its useful to check if everything is working as expected. Open the Terminal in VS Code (Command Palette at top (Ctrl+Shift+P), and type 'View/Toggle Terminal')

1. Get started with

```sh
cd exercises
dune build
# this will show some compiling happening but error due to missing code
```

1. Now you can try out each directory and check if the tests pass. For eg:

```sh
cd 01-introduction
dune runtest
# edit code in the folder until all tests pass!
```

and so on.

## Post workshop details

The contents are made available with a free open source license. Feel free to continue learning OCaml through it and further resources. (We suggest Real World OCaml)

### GitHub Codespaces

Note that GitHub Codespaces are setup by GitHub using your personal GitHub account. While the current gracious free tier limits are more than sufficient for the purposes of this workshop, please consider deleting the codespace once you're done with it. 
You can view/delete your codespaces at https://github.com/codespaces/

If you'd like to continue learning OCaml, setting up a local working setup through the above listed steps is recommended. 

### Further resources

Check out Real World OCaml for learning more about OCaml from the ground up.

## Acknowledgements

- https://github.com/kayceesrk/learn-ocaml-workshop-2024
- https://github.com/janestreet/install-ocaml/blob/master/README.org
- https://github.com/lyrm/bobkonf2026#setup