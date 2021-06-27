# Mac(ARM版)初期設定メモ

## システム環境設定

## `.zprofile` `.zshrc`作成
`.zprofile`を編集
```sh
$ vi ~/.zprofile
```

下記内容を記載
```
if [ -f ~/.zshrc ]; then
    . ~/.zshrc
fi
```

`.zprofile`に実行権限を付与
```sh
$ chmod +x ~/.zprofile
```

下記コマンドで`.zshrc`を作成する
```sh
$ touch ~/.zshrc
$ chmod +x ~/.zshrc
```

## `./vimrc` 作成
```
$ vi ~/.vimrc
```

下記内容を記載
```
syntax on
set nu

set expandtab
set tabstop=2
set shiftwidth=2
set softtabstop=2
set autoindent
set smartindent

set list
set listchars=tab:»-,trail:･,nbsp:･
hi NonText ctermbg=None ctermfg=59 guibg=NONE guifg=None
hi SpecialKey ctermbg=None ctermfg=59 guibg=NONE guifg=None
```

## インストールソフト

### Homebrew
[公式サイト](https://brew.sh/index_ja)よりインストールコマンドを確認し、ターミナルで実行する

※ [正式にARM版に対応したっぽい](https://github.com/Homebrew/install/pull/373)

```sh
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
インストール後下記コマンドを実行する
```
$ echo 'eval $(/opt/homebrew/bin/brew shellenv)' >> /Users/$USER/.zprofile
$ eval $(/opt/homebrew/bin/brew shellenv)
```

※ ARM対応fomula一覧は[こちら](https://github.com/Homebrew/brew/issues/7857)

### Myrica Mフォント
Homebrewでインストール
```sh
$ brew tap homebrew/cask-fonts
$ brew install font-myricam
```

 ### composer
Homebrewでインストール
```sh
$ brew install composer
```

### Visual Studio Code
[公式サイト](https://code.visualstudio.com/)よりダウンロードしてインストール

#### setting.json
```json
{
    "editor.renderWhitespace": "all",
    "editor.fontFamily": "MyricaM M",
    "editor.renderControlCharacters": true,
    "files.insertFinalNewline": true,
    "files.trimFinalNewlines": true,
    "files.trimTrailingWhitespace": true,
    "diffEditor.ignoreTrimWhitespace": false
}
```

#### 拡張機能
下記拡張機能をインストールする
- GitLens
- Project Manager
- Vim
- PHP Inteliephense

#### vimでカーソル移動の長押しが聞かないとき
下記コマンドを入力する
```bash
defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false         # For VS Code
defaults write com.microsoft.VSCodeInsiders ApplePressAndHoldEnabled -bool false # For VS Code Insider
```

### Sublime Text
[公式サイト](http://www.sublimetext.com/)からダウンロードしてインストール

#### install package Control
- `⌘ + ⇧ + p`で`install Pakage control`を入力してPackege Controlをインストールする
- `⌘ + ⇧ + p`で`package Contorl: install Package`と入力、`Alinment`をインストールする

#### vimモードを有効にする
`⌘ + ,`で設定ファイルを開き、`ignored_packages`の`Vintage`を削除する

## その他

### karabiner elements

なんかAppleシリコンMacでカーネルパニックが起きるようになってしまったっぽい
https://github.com/pqrs-org/Karabiner-Elements/issues/2517
fixするまでインストールは見送ることにする
→ MacOs Big Sur 11.3 で解消した

`~/.config/karabiner/karabiner.json`のrulesに下記設定を追加
```json
                    {
                        "description": "viノーマルモード移行時にかなモード解除",
                        "manipulators": [
                            {
                                "from": {
                                    "key_code": "escape"
                                },
                                "to": [
                                    {
                                        "key_code": "escape"
                                    },
                                    {
                                        "key_code": "lang2"
                                    }
                                ],
                                "type": "basic"
                            }
                        ]
                    },
                    {
                        "description": "ctrl + u で escape",
                        "manipulators": [
                            {
                                "from": {
                                    "key_code": "u",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_control"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "escape"
                                    },
                                    {
                                        "key_code": "lang2"
                                    }
                                ],
                                "type": "basic"
                            }
                        ]
                    },
                    {
                        "description": "ctrl + hjkl で 方向キー",
                        "manipulators": [
                            {
                                "from": {
                                    "key_code": "j",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_control"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "down_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "k",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_control"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "up_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "h",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_control"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "left_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "l",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_control"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "right_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "j",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_shift",
                                            "left_control"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "down_arrow",
                                        "modifiers": [
                                            "left_shift"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "k",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_shift",
                                            "left_control"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "up_arrow",
                                        "modifiers": [
                                            "left_shift"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "h",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_shift",
                                            "left_control"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "left_arrow",
                                        "modifiers": [
                                            "left_shift"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "l",
                                    "modifiers": {
                                        "mandatory": [
                                            "left_shift",
                                            "left_control"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "right_arrow",
                                        "modifiers": [
                                            "left_shift"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            }
                        ]
                    }
```
