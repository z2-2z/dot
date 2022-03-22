# Window Manager
```
git clone https://github.com/leftwm/leftwm
cd leftwm
cargo build --release
sudo install -s -Dm755 ./target/release/leftwm ./target/release/leftwm-worker ./target/release/leftwm-state ./target/release/leftwm-check ./target/release/leftwm-command -t /usr/bin
cd ..
sudo cp leftwm.desktop /usr/share/xsessions/
mkdir -p ~/.config/leftwm/themes
rm -f ~/.config/leftwm/themes/current
ln -s $(realpath ./leftwm-theme/) ~/.config/leftwm/themes/current
rm -f ~/.config/leftwm/config.toml
ln -s $(realpath ./leftwm-config.toml) ~/.config/leftwm/config.toml
```

# Terminal Emulator
```
git clone https://github.com/alacritty/alacritty
cd alacritty
cargo build --release --no-default-features --features=x11
sudo cp ./target/release/alacritty /usr/bin
sudo tic -xe alacritty,alacritty-direct extra/alacritty.info
cd ..
mkdir -p ~/.config/alacritty
rm -f ~/.config/alacritty/alacritty.yml
ln -s $(realpath ./alacritty.yml) ~/.config/alacritty/alacritty.yml
```

# Shell
```
git clone https://github.com/ohmyzsh/ohmyzsh
cd ohmyzsh/tools
sh install.sh
cd ../..
rm -f ~/.zshrc
ln -s $(realpath ./zshrc) ~/.zshrc
```

Theme:
```
git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
cd powerlevel10k
mkdir -p ~/.local/share/fonts
pushd ~/.local/share/fonts
wget https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf
wget https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf
wget https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf
wget https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf
popd
```
See `p10k.zsh` for the configuration.

# Application Launcher
```
git clone --depth=1 https://github.com/adi1090x/rofi.git
cd rofi
sh setup.sh
sudo cp ./launcher.sh /usr/local/bin/custom-launcher.sh
```

# Bar
```
git clone https://github.com/polybar/polybar
cd polybar
git submodule update --init
mkdir build
cd build
cmake ..
make
sudo cp bin/polybar* /usr/bin
cd ../..
sudo mkdir -p /etc/polybar
sudo rm -f /etc/polybar/polybar.conf
sudo ln -s $(realpath ./polybar.conf) /etc/polybar/polybar.conf
```

