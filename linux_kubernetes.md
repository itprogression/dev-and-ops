Set up kubectl and helm with auto-completion in Windows Terminal
Cmd.exe does not offer auto-completion while typing. So Windows Subsystem for Linux provides a complete Linux subsystem within Windows. There we can use a common Linux terminal called bash which can be used as an replacement for cmd.exe and powershell with access to windows folders and so on.

Bash completion is a nice feature of the Linux bash which completes scripts while typing and enter tab.

Perquisitions
Docker for Windows
Windows Terminal
Windows-Subsystem für Linux
Installation
Follow the installation instructions of the listed packages above. Enable kubernetes for windows and get familar with the Windows Terminal.

Also install helm for windows and make sure helm is working on Windows.
Open Windows Terminal: “wt.exe”
Open a wsl session
[Optional] Change the user settings so that an admin doesn’t enter a password.
# Edit the sudoers with the visudo command
sudo visudo

# Change the %sudo group to be password-less
%sudo   ALL=(ALL:ALL) NOPASSWD: ALL
Install bash-completion
apt-get install bash-completion
Install kubernetes on wsl
sudo apt-get update && sudo apt-get install -y apt-transport-https gnupg2
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
Add kubernetes completion to bashrc
echo 'source <(kubectl completion bash)' >>~/.bashrc
kubectl completion bash >/etc/bash_completion.d/kubectl
Install helm on wsl
curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
Add helm completion to bashrc
helm completion bash > /etc/bash_completion.d/helm
The Ubuntu folder can be accessed by Windows Explorer by enter the path “\wsl$\Ubuntu-20.04” into path filed of windows explorer.



![image](https://thorstenalpers.github.io/Docs/screenshots/windows-terminal-completion.gif)



