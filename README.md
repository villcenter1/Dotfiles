## My personal dotfiles
forked from jarolrod/vim-python-ide


Table of contents
=================
  * [Getting Started](#getting-started)
    * [Bash](#bash)
    * [Fish](#fish)
    * [DevIcons](#devicons-optional)
    * [Manual Install](#alternatively)
  * [Plugins](#plugins)
    * [Python](#python)
    * [Code + Project Navigation](#code-and-project-navigation)
    * [Snippets](#snippets)
    * [Extra](#extra)
  * [Key Bindings](#key-bindings)
    * [Python](#python)
    * [Switching Between Buffers](#switching-between-buffers)
    * [Toggle Relative Numbering](#toggle-relative-numbering)
    * [Comfortable Motion Scrolling](#comfortable-motion-scrolling)
    * [NerdTree Toggle](#nerdtree-toggle)
    * [Disable Arrow Keys](#disable-arrow-keys)
  
## Getting Started

A script shell will get a copy of the vimrc up and running on your local machine for testing purposes. The script will install the vimrc and compile the YouCompleteMe plugin:
### Bash 
```
Local user
sh -c "$(curl -fsSL https://raw.githubusercontent.com/fire3420/Dotfiles/master/setup.sh)"
Docker user(using jupyter)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/fire3420/Dotfiles/master/setup_docker.sh)"
```
### Fish
```
curl -fsSL https://raw.githubusercontent.com/fire3420/vim-python-ide/master/setup.sh | sh       
```
### YouCompleteMe
YouCompleteMe must be compiled for it to work. The install script handles the compiling, but if something goes wrong then do the following:

1. Make sure the following is included in your vimrc where all the vundle plugins are placed:
```
Plugin 'Valloric/YouCompleteMe'
```

#### MacOS
1. Assuming you already have MacVim installed, install Cmake through brew
```
brew install cmake
```
2. Navigate to YouCompleteMe bundle folder and run the compile script
```
cd ~/.vim/bundle/YouCompleteMe
./install.py --clang-completer
```
3. Reference the [YouCompleteMe](https://github.com/ycm-core/YouCompleteMe) README.md for any other configuration

### Linux
Make sure you have Cmake and Python 3 Headers, they can be downloaded through your distributions package manager. Then run:
```
cd ~/.vim/bundle/YouCompleteMe
python3 ./install.py --clang-completer
```

### DevIcons (Optional)
This plugin is used to show file icons in NerdTree and requires additional steps to install:
* Must install a patched font that contains required glyphs: 
    * [Arch Linux](https://aur.archlinux.org/packages/nerd-fonts-complete/)
    * [Everyone Else](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts)
  * Set vim encoding to UTF-8
    ```
    set encoding=utf8
    ```
  * Set vim font to NerdFont
    ```
    set guifont=<FONT_NAME> <FONT_SIZE>
    ```
  * Add glyphs to Airline
    ```
    let g:airline_powerline_fonts = 1
* If you dont want this feature simply remove this plugin from your vimrc and execute :PluginUpdate in vim, for proper removal delete the devicons plugin folder

### Alternatively:
* Cherry pick the parts you like from my vimrc and add it to yours

## Plugins
* [PEP 8 Indentation](https://github.com/Vimjas/vim-python-pep8-indent) - Python Indentation
* [Jinja](https://github.com/lepture/vim-jinja) - Syntax and Indentation
* [Python Combined](https://github.com/mitsuhiko/vim-python-combined) - Extra handling


### Code and Project Navigation
* [NerdTree](https://github.com/scrooloose/nerdtree) - Project and File navigation
* [Tagbar](https://github.com/majutsushi/tagbar) - Class outline
* [CtrlSpace](https://github.com/vim-ctrlspace/vim-ctrlspace) - Bookmarks/Workspaces/Fuzzy Search/ File management
* [Ack](https://github.com/mileszs/ack.vim) - Search tool
* [Airline](https://github.com/vim-airline/vim-airline) - Tabline
* [Powerline](https://github.com/powerline/powerline) - Used for fonts
* [Fixed Task List](https://github.com/fisadev/FixedTaskList.vim) - Pending tasks
* [Comfortable Motion](https://github.com/yuttie/comfortable-motion.vim) - Physics based scrolling
* [Bookmarks](https://github.com/MattesGroeger/vim-bookmarks) - Bookmark code
* [Indent Guides](https://github.com/nathanaelkane/vim-indent-guides) - Visual repesentation of indents

### Snippets
* [Snippets](https://github.com/honza/vim-snippets) - Snippets
* [Snip-Mate](https://github.com/garbas/vim-snipmate) - Snippet Manager
* [NerdCommenter](https://github.com/scrooloose/nerdcommenter) - Easy code documentation
* [Utility Functions](https://github.com/tomtom/tlib_vim) - Add-on
* [Add-on](https://github.com/MarcWeber/vim-addon-mw-utils) - interpret file by function

### Extra 
* [Sparkup](https://github.com/rstacruz/sparkup) - Condensed HTML parser
* [Riv](https://github.com/Rykka/riv.vim) - Take notes in RST
* [Surround](https://github.com/tpope/vim-surround) - Add parentheses + etc. in pairs
* [Colorscheme](https://github.com/flazz/vim-colorschemes) - Change vim colorscheme
* [Rainbow-Parantheses](https://github.com/kien/rainbow_parentheses.vim) - Rianbow Parentheses
* [Vim-Wiki](https://github.com/vimwiki/vimwiki) - Personal Vim wiki
* [Vimagit](https://github.com/jreybert/vimagit) - Git operations from buffer
* [Dev Icons](https://github.com/ryanoasis/vim-devicons) - File icons in NerdTree
  * [DevIcons Installation](#devicons-optional)

## Key-Bindings
### Python 
```
let g:pymode_run_bind='<F5>'
imap <F5> <Esc>:w<CR>:!clear;python %<CR>
```
### Switching Between Buffers
```
nmap <F9> :bprev<CR>
nmap <F10> :bnext<CR>
```
### Toggle Relative Numbering
```
nnoremap <F4> :set relativenumber!<CR>
```
### Comfortable Motion Scrolling
```
let g:comfortable_motion_scroll_down_key = "j"
let g:comfortable_motion_scroll_up_key = "k"  
```
```
nnoremap <silent> <C-d> :call comfortable_motion#flick(g:comfortable_motion_imp    ulse_multiplier * winheight(0) * 2)<CR>
nnoremap <silent> <C-u> :call comfortable_motion#flick(g:comfortable_motion_imp    ulse_multiplier * winheight(0) * -2)<CR>
nnoremap <silent> <C-f> :call comfortable_motion#flick(g:comfortable_motion_imp    ulse_multiplier * winheight(0) * 4)<CR>
nnoremap <silent> <C-b> :call comfortable_motion#flick(g:comfortable_motion_imp    ulse_multiplier * winheight(0) * -4)<CR>
```

### NerdTree Toggle
* NerdTree wil automatically open when vim is launched in terminal without a file
```
nmap " :NERDTreeToggle<CR>
```
### Disable Arrow Keys
```
no <down> <Nop>
no <left> <Nop>
no <right> <Nop>
no <up> <Nop>

ino <down> <Nop>
ino <left> <Nop>
ino <right> <Nop>
ino <up> <Nop>
                                                                               
vno <down> <Nop>
vno <left> <Nop>
vno <right> <Nop>
vno <up> <Nop>
```

Tmux Key bindings
So ~/.tmux.conf overrides default key bindings for many action, to make them more reasonable, easy to recall and comforable to type.

Let's go through them.

If you are an iTerm2 user, third column describes the keybinding of similar "action" in iTerm2. It's possible to reuse very same keys you already get used to and tell iTerm2 to execute analogous tmux actions. See iTerm2 and tmux integration section below.

tmux key	Description	iTerm2 key
C-a	Default prefix, used instead of "C-b". Same prefix is used in screen program, and it's easy to type. The only drawback of "C-a" is that underlying shell does not receive the keystroke to move to the beginning of the line.	-
<prefix> C-e	Open ~/.tmux.conf file in your $EDITOR	-
<prefix> C-r	Reload tmux configuration from ~/.tmux.conf file	-
<prefix> r	Rename current window	-
<prefix> R	Rename current session	-
<prefix> _	Split new pane horizontally	⌘⇧D
<prefix> |	Split new pane vertically	⌘D
<prefix> <	Select next pane	⌘[
<prefix> >	Select previous pane	⌘]
<prefix> ←	Select pane on the left	⌘⌥←
<prefix> →	Select pane on the right	⌘⌥→
<prefix> ↑	Select pane on the top	⌘⌥↑
<prefix> ↓	Select pane on the bottom	⌘⌥↓
<prefix> C-←	Resize pane to the left	^⌘←
<prefix> C-→	Resize pane to the right	^⌘→
<prefix> C-↑	Resize pane to the top	^⌘↑
<prefix> C-↓	Resize pane to the bottom	^⌘↓
<prefix> >	Move to next window	⌘⇧]
<prefix> <	Move to previous window	⌘⇧[
<prefix> Tab	Switch to most recently used window	^Tab
<prefix> L	Link window from another session by entering target session and window reference	-
<prefix> \	Swap panes back and forth with 1st pane. When in main-horizontal or main-vertical layout, the main panel is always at index 1. This keybinding let you swap secondary pane with main one, and do the opposite.	⌘\
<prefix> C-o	Swap current active pane with next one	-
<prefix> +	Toggle zoom for current pane	⌘⇧Enter
<prefix> x	Kill current pane	⌘W
<prefix> X	Kill current window	⌘⌥W
<prefix> C-x	Kill other windows but current one (with confirmation)	-
<prefix> Q	Kill current session (with confirmation)	-
<prefix> C-u	Merge current session with another. Essentially, this moves all windows from current session to another one	-
<prefix> d	Detach from session	-
<prefix> D	Detach other clients except current one from session	-
<prefix> C-s	Toggle status bar visibility	-
<prefix> m	Monitor current window for activity	-
<prefix> M	Monitor current window for silence by entering silence period	-
<prefix> F12	Switch off all key binding and prefix hanling in current window. See "Nested sessions" paragraph for more info
