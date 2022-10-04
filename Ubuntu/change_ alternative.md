# 01/08/2022
## Problem
Today, I change position of some Python interpreters, then the system cannot understand my command like `python3`
anymore, so I have to config system again.
<br>
And beside, I've installed many interpreters and want to easily change them based on project.

## Solution
- Use `update-alternatives` of Ubuntu
- Change alternatives for system configuration
- Create symbolic link to command at new position

## Code
1. Create new alternative and install an interpreter as an alternative
    ```commandline
    sudo update-alternatives --install <absolute path to new alternative> <alternative name> <absolute path to interpreter> <priority>
    ```
    **Example**
    ```commandline
    sudo update-alternatives --install /usr/bin/python/python3 python3 /usr/bin/python/python3.10 2
    ```
2. Change selection of an alternative when have many interpreters
    ```commandline
    sudo update-alternatives --config <alternative name>
    ```
    Then type password and selection number to finish.
    <br>
    **Example**
    ```commandline
    sudo update-alternatives --config python3
    ```

3. Create symbolic link to command at new position
    ```commandline
    sudo ln -s <path of interpreter> <new path of new link>
    ```
    **Example**
    ```commandline
    sudo ln -s /usr/bin/python/python3.8 /usr/bin/python3
    ```