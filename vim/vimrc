" LOCAL {
" vim: fdl=0: fdm=marker: fmr={,}: mls=2:
function! FoldText()
  return getline(v:foldstart)
endfunction
"setlocal foldtext=FoldText()
setlocal modeline
setlocal fillchars="fold: "
" mmedvede@cs.uml.edu
" }
" VUNDLE SETUP {
" as per www.erikzaadi.com/2012/03/19/auto-installing-vundle-from-your-vimrc/

set nocompatible " Required for Vundle
filetype off " Required for Vundle

" Setting up Vundle - the vim plugin bundler
let vundleAlreadyInstalled=1
let vundle_readme=expand('~/.vim/bundle/vundle/README.md')
if !filereadable(vundle_readme)
  echo "Installing Vundle.."
  echo ""
  silent !mkdir -p ~/.vim/bundle
  silent !git clone https://github.com/gmarik/vundle ~/.vim/bundle/vundle
  let iCanHazVundle=0
endif
set rtp+=~/.vim/bundle/vundle/
call vundle#rc()

" let Vundle manage Vundle, required
Bundle 'gmarik/vundle'

" My bundles
" github:
Bundle 'hynek/vim-python-pep8-indent'
"Bundle 'vim-scripts/LanguageTool'
Bundle 'vim-scripts/DetectIndent'
Bundle 'wojtekmach/vim-rename'
Bundle 'Lokaltog/vim-powerline'
"Bundle 'mmedvede/w3m.vim'
Bundle 'airblade/vim-gitgutter'
" webapi-vim is required by gist-vim
Bundle 'mattn/webapi-vim'
Bundle 'mattn/gist-vim'
Bundle 'chreekat/vim-paren-crosshairs.git'
"Bundle 'aaronbieber/quicktask.git'
Bundle 'tpope/vim-fugitive'
Bundle 'tpope/vim-unimpaired'
Bundle 'tpope/vim-surround'
Bundle 'godlygeek/tabular.git'
Bundle 'scrooloose/nerdcommenter'
"Bundle 'kevinw/pyflakes-vim'
"Bundle 'msanders/snipmate.vim'
Bundle 'altercation/vim-colors-solarized'
Bundle 'majutsushi/tagbar'
Bundle 'avakhov/vim-yaml'
"Bundle 'sgeb/vim-matlab.git'
"Bundle 'vim-scripts/octave.vim--'
"Bundle 'mmedvede/octave.vim'
"Bundle 'jcf/vim-latex.git'
Bundle 'scrooloose/syntastic'
" vim-scripts:
"Bundle 'Rainbow-Parenthesis'
" non github:


if vundleAlreadyInstalled == 0
  echo "Installing Bundles, please ignore key map error messages"
  echo ""
  :BundleInstall
endif

filetype plugin indent on " Vundle required!
" }
" Priority settings (have to be in the beginning){
let mapleader="," " change the mapleader from \ to ,
"}
" PLUGIN SETTINGS {
" DetectIndent{
autocmd BufReadPost * :DetectIndent
" }
" vim-latex {
au BufNewFile,BufReadPre,FileReadPre *.tex let g:Tex_DefaultTargetFormat = 'pdf'
au BufNewFile,BufReadPre,FileReadPre *.ltx let g:Tex_DefaultTargetFormat = 'pdf'
"au BufNewFile,BufReadPre *.tex let g:Tex_FoldedMisc = 'comments'
"
" }
" vim-gist {
let g:gist_show_privates = 1 " List my private gists with :Gist -l
let g:gist_open_browser_after_post = 1
let g:gist_post_private = 1 " Private by default
" }
" Rainbow parens (scheme) {
"runtime bundle/rainbowparens/syntax/RainbowParenthsis.vim
"let loaded_matchparen = 1 "disable paren matching highlight
" }
" Tagbar {
let g:tagbar_usearrows = 1
nnoremap <leader>l :TagbarToggle<CR>
nmap <F8> :TagbarToggle<CR>
" }
" Solarized colorscheme {
set background=dark
let g:solarized_termtrans=1
let g:solarized_termcolors=256
let g:solarized_contrast="high"
let g:solarized_visibility="high"
colorscheme solarized
" }
" Tabular {
if exists(":Tabularize")
  nmap <Leader>a& :Tabularize /&<CR>
  vmap <Leader>a& :Tabularize /&<CR>
  nmap <Leader>a= :Tabularize /=<CR>
  vmap <Leader>a= :Tabularize /=<CR>
  nmap <Leader>a: :Tabularize /:\zs<CR>
  vmap <Leader>a: :Tabularize /:\zs<CR>
endif
" }
" Fugitive {
:command! Gst Gstatus
:command! Gdf Gdiff
:command! Gci Gcommit
" }
" Powerline {
  set encoding=utf-8 " Necessary to show Unicode glyphs
  let g:Powerline_symbols = 'unicode'
  "let g:Powerline_symbols = 'fancy'
  let g:Powerline_mode_n = "N"
  let g:Powerline_mode_v = "V"
  let g:Powerline_mode_i = "I"
" }
" gitgutter{
highlight clear SignColumn
" }
" }
" AUTOCOMMANDS {
" Filetypes and syntax highlight {
au FileType asm source ~/.vim/asm.vim
au BufNewFile,BufRead *ltc3.linux.ibm.com* set filetype=moin
au BufNewFile,BufRead *.launch,*.machine,*.urdf.* set filetype=xml
au BufNewFile,BufRead *gitconfig set filetype=gitconfig
au BufNewFile,BufRead *.rosinstall set filetype=yaml
au BufNewFile,BufRead bashrc*,.vgorc,*/shell/bash/* set filetype=sh
au BufNewFile,BufRead *ssh/*config* set filetype=sshconfig
au BufNewFile,BufRead *rules set filetype=udevrules
au BufNewFile,BufRead *pde set filetype=cpp
au BufNewFile,BufRead *dox set filetype=doxygen
au BufNewFile,BufRead *.m set filetype=octave
"au FileType cpp setlocal foldmethod=syntax
au FileType octave setlocal keywordprg=info\ octave\ --vi-keys\ --index-search
au FileType octave if mapcheck("K","n")!=""|unmap K|endif
au FileType tex syntax spell toplevel " So it checks all text in included latex
" }
" XML Syntax Folding{
let g:xml_syntax_folding=1
"au FileType xml setlocal foldmethod=syntax
" }
set foldmethod=syntax
set foldlevelstart=1

au VimLeave * if filereadable($HOME."/.vim/.netrwhist")|call delete($HOME."/.vim/.netrwhist")|endif " Delete .netrwhist on exit
" Periodically check if file changed and reload {
au CursorHold * checktime
au FileChangedShell  * checktime
au InsertEnter * checktime
au InsertLeave * checktime
au FocusGained * checktime
" }
" }
" NAVIGATION SHORTCUTS {
" tab navigation like firefox {
:nmap <C-S-tab> :tabprevious<CR>
:nmap <C-tab> :tabnext<CR>
:map <C-S-tab> :tabprevious<CR>
:map <C-tab> :tabnext<CR>
:imap <C-S-tab> <Esc>:tabprevious<CR>i
:imap <C-tab> <Esc>:tabnext<CR>i
:nmap <C-t> :tabnew<CR>
:imap <C-t> <Esc>:tabnew<CR>
:map <C-S-t> :tabclose<CR>
" }
" remaps for easier ESC {
imap jj <ESC>
" }
" Deal with wrapped lines {
nnoremap j gj
nnoremap k gk
" }
" Moving between windows {
nmap <silent> <A-Up> :wincmd k<CR>
nmap <silent> <A-Down> :wincmd j<CR>
nmap <silent> <A-Left> :wincmd h<CR>
nmap <silent> <A-Right> :wincmd l<CR>
" }
" Browse through windows {
map <C-J> <C-W>j<C-W>_
map <C-K> <C-W>k<C-W>_
" }
" }
" CONVINIENCE SHORTCUTS {
nmap <silent> <F5> :make<CR>
"nmap <silent> <F6> :!sudo make install <CR>
" ack-grep word under cursor, paste results
nmap <leader>f yaw:r!ack-grep <C-R>"<CR>

" Remove trailing whitespace
nnoremap <Leader>rtw :%s/\s\+$//e<CR>

" Remap tab to C-R completion {
" Insert <Tab> or complete identifier
" if the cursor is after a keyword character
function! MyTabOrComplete()
  let col = col('.')-1
  if !col || getline('.')[col-1] !~ '\k'
    return "\<tab>"
  else
    return "\<C-N>"
  endif
endfunction
inoremap <Tab> <C-R>=MyTabOrComplete()<CR>
" }

" Quickly edit/reload the vimrc file {
nmap <silent> <leader>ev :e $MYVIMRC<CR>
nmap <silent> <leader>sv :so $MYVIMRC<CR>
" }
" Quicker command mode
nnoremap ; :
"auto formatting {
:map <C-S-f> =G
:imap <C-S-f> <ESC>=Gi
" }
" Man pages {
source $VIMRUNTIME/ftplugin/man.vim
nnoremap K :Man <C-R><C-W><CR>
" }
" }
" LOOKS {
" Hidden characters {
" Enable / disable hidden characters
nmap <leader>l :set list!<CR>
set listchars=tab:▸\ ,eol:¬
" }
" Status line {
"
" first, enable status line always
set laststatus=2

" now set it up to change the status line based on mode
if version >= 700
  hi StatusLineNC ctermfg=234 ctermbg=0 gui=bold,reverse
  hi StatusLine ctermfg=235 ctermbg=22 gui=bold,reverse
  au InsertEnter * hi StatusLine ctermfg=235 ctermbg=5 gui=bold,reverse
  au InsertEnter * hi StatusLine ctermfg=235 ctermbg=22 gui=bold,reverse
endif
"set statusline=[%n]\ %<%.99f\ %h%w%m%r%{exists('*CapsLockStatusline')?CapsLockStatusline():''}%y%=%-16(\ %l,%c-%v\ %)%P
set statusline=
set statusline+=%<\                       " cut at start
set statusline+=%2*[%n%H%M%R%W]%*\        " flags and buf no
set statusline+=%-40f\                    " path
set statusline+=%{fugitive#statusline()}  " git info
set statusline+=%=%1*%y%*%*\              " file type
set statusline+=%10((%l,%c)%)\            " line and column
set statusline+=%P                        " percentage of file
" }
" Other {
"set number " Show line numbers
set colorcolumn=+1
hi ColorColumn ctermbg=233
set t_Co=256 " use 256 colors in terminal
hi VertSplit ctermfg=none ctermbg=235 guifg=#060809 guibg=#060809 gui=bold
hi LineNr ctermfg=180  ctermbg=233 guibg=#202025 guifg=#303030
" }
" }
" GENERAL SETTINGS {
" SEARCH {
set incsearch "incremental search
set hlsearch "highlight search
set ignorecase
set smartcase
" }
" Tab completion {
set wildmenu
set wildmode=list:longest,full
" }

set number " Enable line numbers
set shortmess=atI " Shorten status messages, do not show intro when vim starts
set scrolloff=10 " Do not let cursor come close to an edge
set exrc " Allow to use in-folder .vimrc (for per-project settings)
set secure " Required for exrc
set autoread " Automatically refresh file if changed outside vim
set clipboard=unnamed " Use gnome clipboard as default register ("+)
"set nobackup " Disable backup
set noswapfile " Disable swap file
set hidden " Lets us open new file without saving changes
" syntax on reloads colorscheme, overriding any custom color settings
" no need to explicitly enable
"syntax on " Syntax highlighting
filetype plugin indent on
"set modelines=0 "security
set showcmd
set foldmethod=marker
set ttyfast
set ruler " Show line/column of the cursor
set backspace=indent,eol,start "backspace in insert mode
set winminheight=0
"set diffopt+=iwhite " Ignore whitespace in diff
set autoindent "autoindent
set tabstop=2 "tab spaces
set shiftwidth=2
set expandtab "expand tab
set mouse=a " Enable mouse
if has("relativenumber")
  set relativenumber
  hi LineNr ctermfg=236  ctermbg=232
  set cryptmethod=blowfish
  set undofile
  set undodir=~/.vim/tmp
endif
" use single tags file for the whole project
set tags=tags;/
" }
" SPELL CHECK {
set spell spelllang=en_us
setlocal spell spelllang=en_us

"set iskeyword+=-

" Highlight trailing space
match ErrorMsg '\s\+$'

" Spell highlight (should come after all the color schemes are declared)
highlight clear SpellBad
highlight SpellBad term=standout ctermfg=1 term=underline cterm=underline
highlight clear SpellCap
highlight SpellCap term=underline cterm=underline
highlight clear SpellRare
highlight SpellRare term=underline cterm=underline
highlight clear SpellLocal
highlight SpellLocal term=underline cterm=underline

" Ignore CamelCase words when spell checking
fun! IgnoreCamelCaseSpell()
  syn match CamelCase /\<[A-Z][a-z]\+[A-Z].\{-}\>/ contains=@NoSpell transparent
  syn cluster Spell add=CamelCase
  syn match CamelBack /\<[a-z]\+[A-Z].\{-}\>/ contains=@NoSpell transparent
  syn cluster Spell add=CamelBack
  "syn match Misc /\<\S*[\.\-/_0-9]\+\S*\|\u*\>/ contains=@NoSpell transparent
  syn match Misc /\<\a\+[_\/0-9\-@\.]\+\a*\|\u*\>/ contains=@NoSpell transparent
  syn cluster Spell add=Misc
endfun


autocmd BufRead,BufNewFile * :call IgnoreCamelCaseSpell()
" }
