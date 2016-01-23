set nocompatible

execute pathogen#infect()
filetype plugin on                                                          " reenable per filetype loading
syntax enable                                                               " activate syntax highlighting

set history=1000
set hidden
set shell=/usr/bin/env\ bash                                                " load .bashrc when starting shell from Vim
set tabstop=2
set smartindent
set shiftwidth=2
set softtabstop=2
set expandtab
set noswapfile
set ignorecase
set smartcase
set incsearch
set number
set ls=2
noremap gc :!rst2html.py --stylesheet-dirs=~/.config/docutils/css/ --stylesheet-path=base.css,f.css % %:r.html <cr><cr>
noremap gp :w <cr> :!python % <cr>
command! Jade :!jade %
command! Mocha :!mocha --ui tdd
command! Py :!python % -o 
command! Browserify :!Browserify % -o %:p:h/bundle.js
" Pim things
let g:pim_kerberos_bin_dir = '/opt/likewise/bin/'
let g:pim_pig_command = '/export/apps/pig/latest/bin/pig'

augroup extra
  autocmd!
  autocmd BufRead,BufNewFile *.pig set filetype=pig
  autocmd BufRead,BufNewFile *.jade set filetype=jade
augroup END

" source extra vimrc if it exists
let s:extra_vimrc = $HOME . '/.extra/vimrc'
if filereadable(s:extra_vimrc)
  execute 'source ' . s:extra_vimrc
endif

let s:loaded_plugins = 1

" Solarized things.
syntax enable
set background=dark
let g:solarized_termcolors=256
colorscheme solarized

" Ag:
"   :Ag[!] [[OPTIONS] EXPR [FILE ...]]
"
"   Ag for matches of the regexp EXPR. If one or more FILE is specified,
"   only these files are searched, otherwise the entire project directory will
"   be explored. Any matches are loaded in the quickfix window. This
"   implementation is simpler than that of ack.vim
"   (https://github.com/mileszs/ack.vim), uses `ag`, doesn't rely on monkey
"   patching the grep command, and highlights results in the quickfix window.
"
" Arguments:
"   !                                   Load the first match.
"   OPTIONS, EXPR, FILE                 These arguments are forwarded to
"                                       the ag executable (along with the `-H`
"                                       flag to guarantee that the filename
"                                       is always present even when searching
"                                       inside a single file, otherwise the
"                                       quickfix window will fail). Cf.
"                                       `man ag` for details. Note that
"                                       special characters must be escaped or
"                                       quoted. If omitted, the previous ag
"                                       search will be repeated.
"
" Examples:
"   :Ag! hello                          Ag for hello in project directory
"                                       and open first match.
"   :Ag '\bthe\b' %                     Ag for occurrences of the word
"                                       `the` in the current file.
"
command! -bang -nargs=* -complete=file Ag call <SID>ag(<bang>0, <q-args>)
