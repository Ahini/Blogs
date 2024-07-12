---
title: "#!/bin/bash or #!/bin/sh? Are both same or different?"
datePublished: Wed Jul 10 2024 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: clyj4fy4b000309l4cbvd4wwa
slug: binbash-or-binsh-are-both-same-or-different
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720814107704/ca787e0f-60b2-4309-a547-ba9748734870.avif
tags: linux, devops, linux-for-beginners, linux-basics, shell-script, devops-articles, linux-commands, devops-journey, 90daysofdevops, 90daysofdevops-chanllenge, tws, devopscommunity

---

## Day 7 - Shebang `#!/bin/bash` and `#!/bin/sh`

### What are they?

The `#!/bin/bash` and `#!/bin/sh` lines are known as shebang lines. They are used at the beginning of a script to specify the interpreter that should be used to execute the script.

1. **#!/bin/bash**:
    
    * This line tells the system to use the Bash shell (`/bin/bash`) to interpret the script.
        
    * Bash (Bourne Again Shell) is a widely used Unix shell that is the default on many Linux distributions. It provides advanced scripting features, improved command-line editing, and additional built-in commands.
        
2. **#!/bin/sh**:
    
    * This line tells the system to use the Bourne shell (`/bin/sh`) to interpret the script.
        
    * `/bin/sh` often points to the system's default shell, which might be Bash or another shell like Dash (Debian Almquist Shell) on some systems. Scripts written for `/bin/sh` typically use a more basic, portable set of shell features to ensure compatibility across different Unix-like systems.
        

### Differences between `#!/bin/bash` and `#!/bin/sh`

* **Compatibility**:
    
    * Scripts that use `#!/bin/sh` are generally written in a way that is compatible with the original Bourne shell, ensuring they run on various Unix-like systems, even those without Bash.
        
    * Scripts that use `#!/bin/bash` can take advantage of Bash-specific features and enhancements, which may not be compatible with other shells.
        
* **Performance**:
    
    * On some systems, `/bin/sh` is linked to a shell like Dash, which is optimized for performance and uses fewer resources compared to Bash. This can make `#!/bin/sh` scripts execute faster, especially for simple tasks.
        
* **Features**:
    
    * Bash includes additional features like arrays, advanced string manipulation, and improved control structures that are not available in the original Bourne shell. If a script relies on these features, it should use `#!/bin/bash`.
        

### Usage Examples

* **#!/bin/bash**:
    
    ```bash
    #!/bin/bash
    echo "This script is running with Bash"
    for i in {1..5}; do
      echo "Number $i"
    done
    ```
    
* **#!/bin/sh**:
    
    ```bash
    #!/bin/sh
    echo "This script is running with sh"
    for i in 1 2 3 4 5; do
      echo "Number $i"
    done
    ```
    

In summary, you can use `#!/bin/sh` if you want your script to be portable and compatible with a broader range of Unix-like systems. Use `#!/bin/bash` if you need the advanced features provided by Bash and are targeting systems where Bash is available.