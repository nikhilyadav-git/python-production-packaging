### Virtual Environment
- create virtual enev with specific python version
    ```bash
    python3.10 -m venv .venv
    source .venv/bin/activate
    deactivate
    ```

### Multiple Python Versions
- https://docs.python.org/3/
- PEP - Python Enhancement Proposal. PEP is a design document providing information to the Python community, or describing a new feature for Python or its processes or environment.
- PIP - Package Installer for Python
    ```bash
    # Install packages
    pip install package-name 
    # Uninstall packages
    pip uninstall package-name 
    # Upgrade a package
    pip install --upgrade package-name 
    # List installed packages
    pip list 
    # Show package details (version, location, dependencies)
    pip show package-name 
    # Save installed packages to a requirements file:
    pip freeze > requirements.txt 
    # Install packages from a requirements file
    pip install -r requirements.txt
    ```
- __pyenv__ makes managing different Python versions easy.
- https://github.com/pyenv/pyenv
- Add Pyenv startup commands to `~/.zshrc` by running the following in your terminal:
    ```bash
    # brew update
    brew update

    # install pyenv and set zsh config
    brew install pyenv
    brew reinstall pyenv # for upgrade

    # add below in zshrc using - 'source ~/.zshrc' and reload using - 'source ~/.zshrc'       
    ##########################################
    # Load Homebrew (for M1/M2/M3 Macs) 
    eval "$(/opt/homebrew/bin/brew shellenv)"

    # pyenv via Homebrew
    export PYENV_ROOT="$(brew --prefix pyenv)"
    export PATH="$PYENV_ROOT/bin:$PATH"

    # pyenv initialization
    eval "$(pyenv init --path)"
    eval "$(pyenv init -)"
    ##########################################
    
    # show all versions currently installed
    pyenv versions 

    # current set version
    pyenv version 

    # show all availble version available for installtion
    pyenv install --list 
    pyenv install --list | wc -l

    # install version 3.11
    pyenv install 3.11 
    
    # switch to different version
    # current shell/session only
    pyenv shell 3.11 
    python --version 
    > Python 3.11.13

    # all session
    pyenv global 3.11 
    ```

