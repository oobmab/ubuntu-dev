# ubuntu-dev
UbuntuDesktopを使った開発環境構築

```
# vagrant init
# vi Vagrantfile
git clone https://github.com/oobmab/ubuntu-dev.git
cd ubuntu-dev
vagrant up --provider virtualbox
vagrant ssh
```

# ubuntuの日本語化とロケール変更(CUI/GUI共通）
```
sudo locale-gen ja_JP.UTF-8
echo export LANG=ja_JP.UTF-8 >> ~/.profile
source ~/.profile
sudo timedatectl set-timezone Asia/Tokyo
date
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
reboot
```

# chrome
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

# git config
```
git config --global user.name ""
git config --global user.email ""
```

# slack
```
sudo apt install gconf2 gconf-service
wget https://downloads.slack-edge.com/linux_releases/slack-desktop-4.0.2-amd64.deb
sudo dpkg -i slack-desktop-4.0.2-amd64.deb
```

# hyper
```
sudo dpkg -i hyper_3.0.2_amd64.deb
```

# homebrew
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
echo '# set PATH for Homebrew' >> ~/.profile
echo 'eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)' >>~/.profile
source ~/.profile
sudo apt-get install build-essential
```

# npm
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
nvm install 12.11.0
nvm use 12.11.0
```

# tldr
```
npm install -g tldr
```

# yarn
```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install yarn
```

# php
```
brew install php
```

# peek
gifでキャプチャ
```
sudo add-apt-repository ppa:peek-developers/stable
sudo apt update
sudo apt install peek
```

# guake
ターミナル
```
sudo apt install guake
```

# vagrant
```
sudo apt install vagrant
```

# virtualbox
```
sudo apt install virtualbox
```

# その他
```
sudo apt install nkf
sudo apt install ctags
sudo apt install tmux
sudo apt install silversearcher-ag
```
# ruby 環境設定
### rbenv
```
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc

mkdir -p "$(rbenv root)"/plugins
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
sudo apt-get install autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm3 libgdbm-dev libreadline-dev

rbenv install -l
rbenv install 2.6.0
rbenv global 2.6.0
```

### rbenvのアップデート
```
cd ~/.rbenv
git pull
```

### ruby-buildのアップデート
```
cd ~/.rbenv/plugins/ruby-build/
git pull
```

### RubyGemsのアップデート
```
gem update --system
```

# 日本語入力
### fcitx をインストール
```
dpkg-reconfigure keyboard-configuration
cat /etc/default/keyboard
sudo apt-get install fcitx fcitx-mozc
```

### fcitx 設定
「システム設定」>「言語サポート」>「言語」>「キーボード入力に使うIMシステム」の部分で'fcitx'を指定
- Mozc
- キーボード-英語(US)
- キーボード-日本語

# ファイアウォール設定
```
sudo ufw enable
sudo ufw default deny
sudo ufw status verbose 
```

### 22番ポートを解放
```
sudo ufw allow 22
```

# clamav
```
sudo apt install clamav
```

### ウイルススキャンの実行
### ウイルスデータベースを更新
```
sudo /etc/init.d/clamav-freshclam stop
sudo freshclam
sudo /etc/init.d/clamav-freshclam start
```

### ウイルススキャンを実行
```
sudo clamscan --infected --recursive --remove
```

### clamscanのオプションについて
```
--infected: ウイルスに感染したファイルを出力。
--recursive: サブディレクトリを再帰的にスキャン。
--remove: ウイルスに感染したファイルを削除。
```
