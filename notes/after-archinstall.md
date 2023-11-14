
# Instalar Arch Linux (Guia)
## Conectarse a wifi en terminal
  
    nmcli r wifi on  # Prender tarjeta Wifi
    nmcli d wifi list  # Listar redes
    nmcli d wifi connect SSID password PASSWORD # Conetar a red.


## Instalar Session
    
    sudo pacman -S lightdm lightdm-gtk-greeter
    sudo vim /etc/lightdm/lightdm.config 

Modificar/Agregar linea

    greeter-session=lightdm-gtk-greeter

Ejecutar
    
    sudo systemctl enable lightdm.service 

## Instalacion de paquetes necesarios
    
    sudo pacman -S bspwm sxhkd nitrogen picom rofi thunar iw neofetch htop btop alacritty brightnessctl conky wget arandr pulsemixer git polybar zsh nvim lsd bat zsh-autosuggestions zathura

## Definir variable Home

Abrir/Crear archivo .profile
    nvim .profile
  
Escribir/Modificar:

    XDG_CONFIG_HOME="$HOME/.config"
    export XDG_CONFIG_HOME 

## Bootear s.o con  bspwm sxhkd
Abir/Crear .xprofile

    nvim .xprofile

Escribir/Modificar:

    sxhkd &
    exec bspwm

Copiar configuracion por defecto

    mkdir .config
    cd .config
    mkdir bspwm
    mkdir sxhkd
    cp /usr/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm/
    cp /usr/share/doc/bspwm/examples/sxhkdrc ~/.config/sxhkd/

Poner alacritty como terminal 

    nvim ~/.config/sxhkd/sxhkdrc

Escribir/Modificar:

  #terminal emulador
  super + Return
      alacritty

Poner zsh por defeto
    chsh -s /bin/zsh

Reiniciar
    reboot

## Agrear repositorio AUR
    sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si

## Agregar fuentes utilizadas (opcional)

    mv fonts/* usr/share/fonts/TTF 

Agregar la fuente en Alacritty (opcional)

    nvim ~/.config/alacritty/alacritty.yml

Escribir/Modificar:

  font:
    normal:
      family: "MesloLGS NF"

# Programas
## Instalar Rofi

    mkdir /home/soshi/.local/share/rofi/ 
    mkdir /home/soshi/.local/share/rofi/themes
    mv spotlight-dark.rasi /home/soshi/.local/share/rofi/themes/

## Instalar Office
    
    yay -S onlyoffice-bin

## Paquetes ZSH
  oh-my-zsh:
    
    wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh && sh install.sh

  powerlevel10k(hacer):

    git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k 

  zsh-syntax-highlighting:

    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

  zsh-autosuggestions (hacer):
    
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
## LunarVIm
LunarVim:
    
    sudo pacman -S git make python python-pip npm nodejs cargo
    su
    LV_BRANCH='release-1.3/neovim-0.9' bash <(curl -s https://raw.githubusercontent.com/LunarVim/LunarVim/release-1.3/neovim-0.9/utils/installer/install.sh)
  
Inside LunarVim :LvimUpdate
Inside LunarVim :LvimSyncCorePlugins

## VisualStudio
    
    yay -S visual-studio-code-bin

## Eclipse
    
    sudo pacman -S jdk11-openjdk
Descargar instalador, descomprimir y ejecutarlo

## NvChad
git clone https://github.com/NvChad/NvChad ~/.config/nvim --depth 1 && nvim

Inside nvim :NvChadUpdate
