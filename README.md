<p align="center"><a href="https://github.com/hacklexander/LICENSE"><img src="https://img.shields.io/static/v1.svg?style=flat-square&label=License&message=GPL-3.0&logoColor=eceff4&logo=github&colorA=1A1B26&colorB=blue"/></a></p>



# My configuration BSPWM in Arch 



<img src="https://i.redd.it/f5vu2auetgxz.png" alt="Linux Fetch" align="right" width="350">

|    Distro    |                                               [Arch](https://archlinux.org/)                                                |
| :----------: | :-------------------------------------------------------------------------------------------------------------------------: |
|      WM      |                                        [BSPWM](https://github.com/baskerville/bspwm)                                        |
|     Bar      |                                        [Polybar](https://github.com/polybar/polybar)                                        |
|     Menu     |                                         [Rofi](https://github.com/davatorium/rofi)                                          |
|  Compositor  |                               [Picom](https://archlinux.org/packages/community/x86_64/picom/)                               |
|   Terminal   |                               [Kitty](https://archlinux.org/packages/community/x86_64/kitty/)                               |
|   Widgets    |                                  [ElKowars wacky widgets ](https://github.com/elkowar/eww)                                  |
| Music/Player | [mpd](https://archlinux.org/packages/extra/x86_64/mpd/)-[ncmpcpp](https://archlinux.org/packages/community/x86_64/ncmpcpp/) |
| File Manager |                              [Nautilus](https://archlinux.org/packages/extra/x86_64/nautilus/)                              |
|    Shell     |                                   [Zsh](https://archlinux.org/packages/extra/x86_64/zsh/)                                   |  |


---
---


| <img src="misc/readme/primer-parte.gif" alt="video 1" align="center" width="350px"> | <img src="misc/readme/segunda-parte.gif" alt="video 2" align="center" width="350px"> |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |

<details>
<summary><b>Mas fotos</b></summary>

| <img src="misc/readme/calendar.png" alt="calendar" align="center" width="200px"> | <img src="misc/readme/rofi.png" alt="Rofi" align="center" width="200px"> | <img src="misc/readme/dashboard.png" alt="Dashboard" align="center" width="200px"> |
| -------------------------------------------------------------------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------------- |

</details>

---

# 📦 Instalacion dependencias

Lo primero que debemos hacer es instalar todas las dependencias que necesitaremos para que la configuracion funcione correctamente y sin errores. 

>Tenga en cuenta que debemos tener instalado git antes que todo, si no lo tiene instalado solo escriba este comando en consola: **`sudo pacman -S git`**

Instalacion de AUR Helper  **`yay`**:

```bash
cd $HOME
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si --noconfirm
cd ..
rm -rf yay
```

Instalamos todos los paquetes necesarios:

```bash
yay -Syy polybar sxhkd todotxt xclip kitty \
		brightnessctl dunst rofi lsd bat jq \
		xfce-polkit playerctl mpd nautilus \
		ncmpcpp ranger mpc picom xfce4-power-manager-git \
		feh ueberzug maim pamixer libwebp \
		webp-pixbuf-loader xorg-xprop xorg-xkill \
		physlock papirus-icon-theme betterlockscreen zsh \
		zsh-autosuggestions zsh-history-substring-search \
		zsh-syntax-highlighting zsh-theme-powerlevel10k
```

Habilitamos servicios:

```bash
sudo systemctl enable mpd.service
sudo systemctl start mpd.service
```

---

# 📦 Instalacion Dotfiles

Posteriormente a esto lo que tendremos que hacer un git clone para descargar el repositorio y tenerlo localmente, aconsejo clonarlo en la carpeta **`/tmp`**, los comandos son los siguientes:

```bash
cd /tmp
git clone https://github.com/hacklexander/dotfiles-bspwm.git
cd dotfiles-bspwm/
```

Una vez tengamos el repositorio de manera local, lo que tenemos que hacer es copear las carpetas del directorio **`config/`**, los comandos son lo siguientes:

```bash
cp -r config/* ~/.config
```

Ahora haremos lo mismo con el direcorio **`fonts/`**:

```bash
mkdir -p ~/.fonts
cp -r fonts/* ~/.fonts
```

Copiamos el directorio **`bin/`** en **`$HOME/.local/bin`**:

```bash
cp -r bin/* ~/.local/bin
```

Copiamos los archivos de configuracion que esta en **`home/`** 

```bash
cp -r home/* $HOME
```

---

Estas configuraciones estan basadas mayormente en los dotfiles de ***[gh0stzk](https://github.com/gh0stzk/dotfiles)*** y de ***[rxyhn](https://github.com/rxyhn/tokyo)***, dejo los creditos correspondientes, tambien hay configuraciones personales, puede que a todos no les guste, pero no esta de mas que las puedan probar y darme su opinion constructiva.