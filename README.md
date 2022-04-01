# My Configs

## Tmux config

Install tmux plugin manager

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```


**tmux-power**

```vim-script
# Send prefix
set-option -g prefix C-a
unbind-key C-a
bind-key C-a send-prefix

# Use Alt-arrow keys to switch panes
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Shift arrow to switch windows
bind -n S-Left previous-window
bind -n S-Right next-window


# Set easier window split keys
bind-key v split-window -h
bind-key h split-window -v

# Easy config reload
bind-key r source-file ~/.tmux.conf \; display-message "tmux.conf reloaded"


set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

set -g @plugin 'wfxr/tmux-power'
set -g @plugin 'wfxr/tmux-net-speed'
set -g @plugin 'wfxr/tmux-prefix-highlight'
set -g @plugin 'wfxr/tmux-web-reachable'
set -g @tmux_power_theme 'coral'
set -g @tmux_power_date_format '%F'
set -g @tmux_power_time_format '%T'
set -g @tmux_power_date_icon '📅'
set -g @tmux_power_time_icon '🕘' # emoji can be used if your terminal supports
set -g @tmux_power_user_icon '🔑'
set -g @tmux_power_session_icon '💻'
set -g @tmux_power_upload_speed_icon '↑'
set -g @tmux_power_download_speed_icon '↓'
set -g @tmux_power_show_upload_speed true
set -g @tmux_power_show_download_speed true
set -g @tmux_power_show_web_reachable true
# 'L' for left only, 'R' for right only and 'LR' for both
set -g @tmux_power_prefix_highlight_pos 'LR'

run '~/.tmux/plugins/tpm/tpm'
```


## Neovim config

install neovim

```bash
wget https://github.com/neovim/neovim/releases/download/v0.6.1/nvim-linux64.tar.gz
```

install pynvim
```bash
pip install pynvim
```
install vim-plug
```bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

install copilot
```bash
git clone https://github.com/github/copilot.vim.git ~/.config/nvim/pack/github/start/copilot.vim
```

install nvm and node
```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
nvm install node
```


```vim-script

syntax on
let mapleader=" "
set number
set norelativenumber
set cursorline
set wrap
set showcmd
set wildmenu
set hlsearch
set incsearch
exec "nohlsearch"
set ignorecase
set smartcase
set noshowmode

noremap i k
noremap j h
noremap k j
noremap l l
noremap <LEADER><CR> :nohlsearch<CR>

noremap h i
noremap H I

map S :w<CR>
map Q :q<CR>
map R :source $MYVIMRC<CR>

call plug#begin()
Plug 'preservim/nerdtree'
Plug 'folke/tokyonight.nvim', { 'branch': 'main' }
Plug 'itchyny/lightline.vim'
Plug 'Xuyuanp/nerdtree-git-plugin'
Plug 'Raimondi/delimitMate'
Plug 'karb94/neoscroll.nvim'
Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins' }
Plug 'zchee/deoplete-jedi'
call plug#end()
exec "colorscheme tokyonight"
let g:lightline = {
        \ 'colorscheme': 'tokyonight',
        \ 'active': {
        \       'left': [['mode', 'paste'],
        \                ['gitbranch', 'readonly', 'filename', 'modified', 'helloworld']]
        \       },
        \ 'component': {
        \       'helloworld': 'Hello, world!',
        \       },
        \ 'component_function': {
        \       'gitbranch': 'FugitiveHead'
        \       },
        \ }
nnoremap <learder>n :NERDTreeFocus<CR>
nnoremap <C-n> :NERDTree<CR>
nnoremap <C-t> :NERDTreeToggle<CR>

let g:NERDTreeGitStatusIndicatorMapCustom = {
    \ "Modified"  : "✹",
    \ "Staged"    : "✚",
    \ "Untracked" : "✭",
    \ "Renamed"   : "➜",
    \ "Unmerged"  : "═",
    \ "Deleted"   : "✖",
    \ "Dirty"     : "✗",
    \ "Clean"     : "✔︎",
    \ "Unknown"   : "?"
    \ }

let g:python3_host_prog = '/opt/anaconda3/bin/python'
# remember to change to your own python location
let g:deoplete#enable_at_startup = 1
let g:deoplete#auto_complete = 1
let g:deoplete#sources#jedi#show_docstring = 1
let g:deoplete#sources#jedi#python_path = '/opt/anaconda3/bin/python'

```




