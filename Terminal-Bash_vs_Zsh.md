### Shell Basics
- Bash
    - Stands for Bourne Again Shell
    - Most common Unix shell
    - Great for scripting
    - Supported nearly everywhere
- Zsh
    - Stands for Z Shell
    - Includes all Bash features + more
    - Better autocomplete, plugins, and themes
    - Default shell in macOS Catalina (10.15) and later

### Switching Shell (Temporary)
- You can start a different shell for the current terminal session by typing below commands. This change is temporary and lasts only until you close the terminal window.
    ```bash
    # Switch to Zsh
    zsh
    
    # Switch to Bash
    bash
    ```

### Check the current shell in use:
- This shows the current shell interpreter for that session.
    ```bash
    echo $0
    ```

### Check the current default shell:
- This shows the current shell interpreter for that session.
    ```bash
    echo $SHELL
    
    # expected output
    /bin/zsh → Zsh is active
    # or
    /bin/bash → Bash is active
    ```

### Set Shell Permanently
- Check Available Shells
    ```bash
    cat /etc/shells
    
    # output
    /bin/bash
    /bin/zsh
    ```
- Change Default Shell
    ```bash
    # Run one of the following:
    
    # Set Zsh as default
    chsh -s /bin/zsh

    # Set Bash as default
    chsh -s /bin/bash

    # If that doesnot work, try specifying your user:
    # Replace `$(whoami)` with your username if needed
    chsh -s /bin/zsh $(whoami)
    ```

### ohmyzsh
- https://ohmyz.sh/
- update Zsh theme, ZSH_THEME=__"bira"__
    ```bash
    ~ code ~/.zshrc
    # restart terminal
    ~ zsh
    ```
- Enable/Disable Plugins 
    - List of plugins 
        ```bash
        ls ~/.oh-my-zsh/plugins/
        ```
    - Update, plugins=(git) to add new plugins i.e. plugins=(git web-search)
        ```bash
        ~ code ~/.zshrc
        # restart terminal
        ~ zsh
        # test plugin
        ~ google "cricbuz"
        ~ stackoverflow "dunder in python"
        ```
    - To disable the plugin just remove entry from the plugins list i.e. plugins=(git web-search) to plugins=(git)
    - Custom plugins - Add the plugin to the list of plugins for Oh My Zsh to load (inside ~/.zshrc) plugins=(# other plugins... zsh-autosuggestions zsh-syntax-highlighting)
        ```bash
        ~/.oh-my-zsh/custom/plugins

        google "zsh autosuggestions github"
        git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

        google "zsh syntax highlighting plugin github"
        git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
        ```