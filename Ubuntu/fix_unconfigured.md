# 04/10/2022
## Problem
Today, I want to install `ncdu` with `sudo apt install ncdu`
<br>
But unfortunately, I've faced problems with unconfigured and half configured packages
```commandline
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on language-selector-gnome (>= 0.179~); however:
  Package language-selector-gnome is not configured yet.
```

## Solution
- Try to configure those packages
- If you cannot do that, remove or move file of that package and re-install

## Code
1. List package which is not fully configured
    ```commandline
    sudo dpkg --audit
    ```
2. Try to configure each specific package
    ```commandline
    sudo dpkg --configure <package-name>
    ```

    If you cannot configure, you may know that:
   - The packages it is depends on is not fully configured, or
   - There is an error when configure it
   
    If this is the case, move to next step

3. Make a backup folder
    ```commandline
    sudo mkdir ~/backup
    ```
   
4. Move all file of that package to the backup folder
    ```commandline
    sudo mv /var/lib/dpkg/info/<package-name>* ~/backup
    ```
   
5. Try to configure package again
    ```commandline
    sudo dpkg --configure -D 777 <package-name>
    ```

6. After finish configure all package, remove backup folder
    ```commandline
    sudo rm -r ~/backup
    ```