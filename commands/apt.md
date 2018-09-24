# APT

## [Tip] List & Install a Specific Package Version

### Description

Sometimes you may want to install a specific package version. So you'll need first to see what versions are available to you from your package repositories and then install the one you want.

### Solution

Use this command to list available package versions:

    sudo apt-cache policy <package_name>

For example, Firefox:

    mhsabbagh@mysimplepc:~/$ sudo apt-cache policy firefox
    firefox:
      Installed: 62.0+linuxmint1+tara
      Candidate: 62.0+linuxmint1+tara
      Version table:
     *** 62.0+linuxmint1+tara 700
            700 http://packages.linuxmint.com tara/upstream amd64 Packages
            100 /var/lib/dpkg/status
         62.0+build2-0ubuntu0.18.04.5 500
            500 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
            500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
         59.0.2+build1-0ubuntu1 500
            500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages

And to install a specific package, put the **=** symbol in between the package name and the version:

    sudo apt install firefox=62.0+build2-0ubuntu0.18.04.5