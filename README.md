# MacOS Ansible Playbook

This ansible playbook will install/configure most of the software on a new mac. There are still some manual steps needed.
Based heavily on https://github.com/geerlingguy/mac-dev-playbook

# Installation
1. Configure the initial setup of iCloud and App store (if using different apple accounts)
2. Install command line tools
```
xcode-select --install
```
3. Install Rosetta
```
/usr/sbin/softwareupdate --install-rosetta
```
4. Install Homebrew
```
cd ~
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/$USER/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```
5. Create symlink for iCloud Documents

Can be done later, originally was storing the initial BrewFile for git/mas apps
```
ln -s "/Users/$USER/Library/Mobile Documents/com~apple~CloudDocs" iCloud
```
6. Install git and mas
```
brew install git
brew install mas
```
7. Create project directories for git repositories
```
mkdir -p ~/projects/{work,personal}
```
8. Install Ansible
```
export PATH="$HOME/Library/Python/3.8/bin:/opt/homebrew/bin:$PATH"
pip3 install --upgrade --user pip
pip3 install ansible --user
```
9. Clone repository
```
cd ~/projects/work && \
  git clone 
```
10. Copy config.yml

Copy your config.yml into the vars folder of the playbook. If it's not present, the file vars/default.config.yml will be used

11. Run the playbook ```ansible-playbook main.yml```
