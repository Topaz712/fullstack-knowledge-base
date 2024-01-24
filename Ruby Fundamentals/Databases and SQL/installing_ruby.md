# Installing Ruby How-to

- Based on Code coach Nolan's video and Code coach German's notes on it

## Windows

- In windows search bar, search Turn Windows features on or off

  - Check Windows Subsystem for Linux
  - Check Virtual Machine Platform
  - Check Windows Hypervisor Platform
  - Click ok

- Restart computer to apply changes

- Run Windows Powershell or windows command prompt as an administrator

- In the terminal, run `wsl --install -d Ubuntu` it may ask you to make an account, Make an account and remember the password. An Ubuntu terminal should open up.

  - Will not be able to see password when typing, that is on purpose, for security, but you will be asked to retype for verification

- Go to (https://rvm.io/rvm/install)[https://rvm.io/rvm/install]

  - On the website, where it says '_Install GPG keys_', copy the command and enter it into the ubuntu terminal. Continue even if you get errors. It might not work, if so, then do the following:
    - Go to (https://rvm.io/rvm/security)[https://rvm.io/rvm/security] or just click on word **securtiy** right under that command, then under alternatives, copy and paste the two commands into the ubuntu terminal one by one

- Enter `\curl -sSL https://get.rvm.io | bash` in your Ubuntu terminal.

- Restart the terminal and search for 'ubuntu' or also called 'wsl' in your windows finder

- Enter `rvm -v` to check if rvm is installed
  - Can also enter `rvm list rubies` to see which rubies versions you currently have installed in your system
  - Can also enter `rvm list known` to see all the rubies there are
    - For us, we will be looking at the **# MRI Rubies** list which is at the top and then look at the last ruby listed as that is the most recent
- Enter `rvm install ruby 3.2.0`

- Open VS Code (restart if already open) and open a new terminal. The terminal needs to be the Ubuntu terminal to access ruby.

  - Once, open enter ruby -v to check if ruby is installed.

- In the video, coach Nolan talks about how **we want to do this in VSCode so we will need to open our wsl terminal**

  - We want to be in our wsl terminal anytime we're coding in Ruby, always be in wsl
    - An an example , Nolan creates a directory called 'mkdir Ruby'
    - Then types 'cd Ruby'
    - Then types 'code .' to open this directory in vscode
    - This opens vscode and he creates a file called main.rb , in that file tests it by typing 'puts "Hello World"'
      - Then in vscode terminal, clicks dropdown and chooses the ubuntu(wsl) option which will let us use a WSL terminal inside of vs code now that we have it installed
      - After this he tests that we have ruby installed by running command 'ruby main.rb' in terminal and it prints out the string

## Mac

- Go to https://brew.sh/

- Copy the command from the website and enter it into your terminal.

- Once installed, run brew install gnupg gnupg2

- Once installed run, sudo xcode-select --install, click install on the pop up.

- Restart your computer.

- Go to https://rvm.io/rvm/install

- On the website, where it says 'Install GPG keys', copy the two commands and enter it into the terminal. Continue even if you get errors. It might not work.

- Go to https://rvm.io/rvm/security, under alternatives, copy and paste the commands into the terminal.

- Enter \curl -sSL https://get.rvm.io | bash in your Ubuntu terminal.

- Restart the terminal and Enter rvm -v to check if rvm is installed

- Enter rvm install ruby 3.2.0

- Open VS Code (restart if already open) and open a new terminal.

- Once, open enter ruby -v to check if ruby is installed.
