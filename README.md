# Physikpraktikum-1-iING
Python für das Physikpraktikum 

# Setting Up An Environment

## (Optional) Installing [Chocolatey](https://docs.chocolatey.org)

Chocolatey is a package manager for Windows making installing and maintaining Software easy, repeatable and even scriptable.

Following install instructions can be found at the official chocolatey [setup guide](https://docs.chocolatey.org/en-us/choco/setup). To install open Power Shell with admin privileges. To do so press windows key <kbd>❖ Win</kbd> + <kbd>X</kbd> and pick Windows PowerShell (Admin) like shown in the picture below.

<img src="assets\run_pshell_admin.png" alt="image" width="200" height="auto">

After accepting the UNC prompt a PowerShell window should appear. Copy and paste the following line and accept policy change with <kbd>Y</kbd> and <kbd>Enter</kbd>:

```
Set-ExecutionPolicy AllSigned
```
Finally, run the following command:
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

Now, if ``choco --version`` returns with no errors you are all set :confetti_ball:

## Git

Git is **the** got-to tool for source control and management. From the [official website](https://git-scm.com/):

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

### Install With Chocolatey

If Chocolatey was installed previously, installing Git is done by running the following command:

```
choco install git --params="'/NoAutoCrlf /NoShellIntegration /DefaultBranchName:main'" -y
```

### Install Without Chocolatey

Go to Git's [download](https://git-scm.com/download/win) page for Windows and download the appropriate standalone installer - most likely 64-bit. Run the downloaded executable and disable *Windows Explorer integration* to not have Git clutter your right-click menu. Hit next and accept all other defaults.

<img src="assets\git_setup_options.png" alt="image" width="50%" height="auto">

## Miniconda

### Install With Chocolatey

```
choco install miniconda3 --params="'/InstallationType:JustMe' '/RegisterPython:1' '/AddToPath:0'" -y
```

Heads up :point_up:: use below command instead if you already have a working Python install to not have miniconda overwrite your primary Python interpreter. 

```
choco install miniconda3 --params="'/InstallationType:JustMe' '/RegisterPython:0' '/AddToPath:0'" -y
```

### Install Without Chocolatey

Visit [minicondas](https://docs.anaconda.com/free/miniconda/index.html) download page and download the latest Windows installer. Run the installer and keep all default settings.

Heads up :point_up:: disable *"Register Miniconda3 as my default Python 3.12"* if you already have a working Python install to not have miniconda overwrite your primary Python interpreter.
<img src="assets\miniconda_setup_options.png" alt="image" width="50%" height="auto">

## VSCode

## Jupyter Kernel