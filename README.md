# Physikpraktikum-1-iING
Python für das Physikpraktikum 

# Setting Up An Environment

## (Optional) Installing [Chocolatey](https://docs.chocolatey.org)

Chocolatey is a package manager for Windows making installing and maintaining Software easy, repeatable and even scriptable.

Following install instructions can be found at the official chocolatey [setup guide](https://docs.chocolatey.org/en-us/choco/setup). To install open Power Shell with admin privileges. To do so press windows key <kbd>⊞ Win</kbd> + <kbd>X</kbd> and pick Windows PowerShell (Admin) like shown in the picture below.

<img src="assets\run_pshell_admin.png" alt="image" width="200px" height="auto">

After accepting the UNC prompt a PowerShell window should appear. Copy and paste the following line and accept policy change with <kbd>Y</kbd> and <kbd>↵ Enter</kbd>:

```PowerShell
Set-ExecutionPolicy AllSigned
```

Finally, run the following command:

```PowerShell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

Now, if ``choco --version`` returns with no errors you are all set :confetti_ball:

## Git

Git is **the** got-to tool for source control and management. From the [official website](https://git-scm.com/):

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

### Install With Chocolatey

If Chocolatey was installed previously, installing Git is done by running the following command:

```PowerShell
choco install git --params="/NoAutoCrlf /NoShellIntegration /DefaultBranchName:main" -y
```

### Install Without Chocolatey

Go to Git's [download](https://git-scm.com/download/win) page for Windows and download the appropriate standalone installer - most likely 64-bit. Run the downloaded executable and disable *Windows Explorer integration* to not have Git clutter your right-click menu. Hit next and accept all other defaults.

<img src="assets\git_setup_options.png" alt="image" width="400px" height="auto">

## Miniconda

### Install With Chocolatey

```PowerShell
choco install miniconda3 --params="/InstallationType:JustMe /RegisterPython:1 /AddToPath:0" -y
```

Heads up :point_up:: use below command instead if you already have a working Python install to not have miniconda overwrite your primary Python interpreter. 

```PowerShell
choco install miniconda3 --params="/InstallationType:JustMe /RegisterPython:0 /AddToPath:0" -y
```

### Install Without Chocolatey

Visit [minicondas](https://docs.anaconda.com/free/miniconda/index.html) download page and download the latest Windows installer. Run the installer and keep all default settings.

Heads up :point_up:: disable *"Register Miniconda3 as my default Python 3.12"* if you already have a working Python install to not have miniconda overwrite your primary Python interpreter.
<img src="assets\miniconda_setup_options.png" alt="image" width="400px" height="auto">

## Visual Studio Code

We will use [Visual Studio Code](https://code.visualstudio.com/) or VSCode for short as our IDE (integrated development environment) i.e. the tool to create and/or edit the actual Jupyter notebooks. VSCode is not to be mistaken for the full blown Visual Studio.

### Install With Chocolatey

At this point you should already know the drill:

```PowerShell
choco install vscode -y
```

After successfull install run the command:
```PowerShell
code --install-extension ms-toolsai.jupyter ms-python.python ms-toolsai.jupyter-renderers alefragnani.project-manager
```

This will add some useful extension to VSCode we will need later on.

### Install Without Chocolatey

[Download](https://code.visualstudio.com/) and run the Windows installer keeping all defaults.

## Pulling the Repository Files

<!-- Click on the green button at the top of this page. Copy the https-link from the new window to the clipboard.

<img src="assets\repo_copy_url.gif" alt="image" width="75%" height="auto"> -->

Press the Windows key <kbd>⊞ Win</kbd>, type ``Git Bash`` and hit enter. The Git Bash window should open. The default location is the users profile directory ``C:\Users\<username>``. ``cd`` (change directory) into a directory of your liking - here, we ``cd`` into ``C:\Users\<username>\Documents``.

Enter the commands:

```bash
git clone https://github.com/SusannaGa/Physikpraktikum-1-iING.git
cd Physikpraktikum-1-iING
code .
```

This will create a new directory named ``Physikpraktikum-1-iING`` and download everything into it. We will ``cd`` into the new directory and start VSCode inside it. The GIF below shows how the process should look like.

<img src="assets\repo_clone.gif" alt="image" width="400px" height="auto">

Phew, lots of stuff happened until now but bear with me, we are almost there :muscle:

## Creating a Virtual Python Environment

Issues could and will arise if different Python and/or Python library versions are used. To prevent this we use miniconda to create so-called "virtual environments" in a predictable and consistent manner. This way you, me, we all work with the exact same versions of all relevant files making troubleshooting a whole lot easier. Press <kbd>⊞ Win</kbd>, type Anaconda Prompt and hit <kbd>↵ Enter</kbd>.

<img src="assets\run_anaconda_prompt.png" alt="image" width="400px" height="auto">

Inside the new terminal window run the following commands:

```bash
conda create -n physikpraktikum1 python=3.12 -y
conda activate physikpraktikum1
```

The first line creates a new environment with the name ``physikpraktikum1`` and installs Python with the specific version 3.12 in it. The second line activates the freshly created environment. The prompt should now begin with something like ``(physikpraktikum1) C:\Users\yourusername>``.

No longer needed environments can be removed using the command:
```
conda remove -n <environment name> --all
```