## Piaware package for Arch Linux and AlarmPi
### Builds Piaware package consisting of following components in a single package:</br>
- Piaware
- faup1090
- fa-mlat-client

## 1 - Prepration </br>
### 1.1 - Install tools required to build packages - First thing to be done before attempting to build ANY package </br>
`sudo pacman --needed -Sy fakeroot binutils git autoconf gcc make patch `
</br>
### 1.2 - Install dependencies available in Arch Linux Repository </br>
`sudo pacman --needed -Sy tcl python tk  `
</br>
### 1.3 - Build and Install depencies not available in repository.</br>
NOTE: Building these requires build tools (item 1.1 and 1.2 above) to be installed first.</br>

**1.3.1 - tcllib** </br>
```
git clone https://aur.archlinux.org/tcllib  
cd tcllib  
makepkg -si  
cd ../  
```

**1.3.2 - tclx** </br>

```
git clone https://aur.archlinux.org/tclx  
cd tclx  
makepkg -si  
cd ../  
```

**1.3.3 - tcltls** </br>
```
git clone https://aur.archlinux.org/tcltls  
cd tcltls  
makepkg -si  
cd ../  
```

**1.3.4 - tcllauncher** </br>
```
git clone https://aur.archlinux.org/tcllauncher  
cd tcllauncher  
makepkg -si  
cd ../  
```
</br>

## 2 - Build Piaware package: </br>

```
git clone https://github.com/abcd567a/piaware-arch   
cd piaware-arch   
makepkg -si  
cd ../  
```
