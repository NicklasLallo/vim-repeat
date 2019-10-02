# repeat.vim

If you've ever tried using the `.` command after a plugin map, you were
likely disappointed to discover it only repeated the last native command
inside that map, rather than the map as a whole.  That disappointment
ends today.  Repeat.vim remaps `.` in a way that plugins can tap into
it.

The following plugins support repeat.vim:

* [surround.vim](https://github.com/tpope/vim-surround)
* [speeddating.vim](https://github.com/tpope/vim-speeddating)
* [unimpaired.vim](https://github.com/tpope/vim-unimpaired)
* [vim-easyclip](https://github.com/svermeulen/vim-easyclip)
* [vim-radical](https://github.com/glts/vim-radical)

Adding support to a plugin is generally as simple as the following
command at the end of your map functions.

    silent! call repeat#set("\<Plug>MyWonderfulMap", v:count)

## Fork
This fork changes two things:
* It disables the default maps for u, U, & ctrl+r. To restore them use:
```
nmap u <Plug>(RepeatUndo)
nmap U <Plug>(RepeatUndoLine)
nmap <C-R> <Plug>(RepeatRedo)
```
* It adds a optional wrapper that supports remapping so that you can use other functions together with this:
```
    nnoremap <silent> u     :<C-U>call repeat#wrapMod("\<Plug>(highlightedundo-undo)",v:count)<CR>
```
This is mainly useful when you want to chain u, U, & ctrl+r together with other plugins and vim-repeat without breaking vim-repeat. For other use cases `repeat#set()` should be sufficient.

## Installation

Install using your favorite package manager, or use Vim's built-in package
support:

    mkdir -p ~/.vim/pack/tpope/start
    cd ~/.vim/pack/tpope/start
    git clone https://tpope.io/vim/repeat.git

## Contributing

See the contribution guidelines for
[pathogen.vim](https://github.com/tpope/vim-pathogen#readme).

## Self-Promotion

Like repeat.vim? Follow the repository on
[GitHub](https://github.com/tpope/vim-repeat) and vote for it on
[vim.org](http://www.vim.org/scripts/script.php?script_id=2136).  And if
you're feeling especially charitable, follow [tpope](http://tpo.pe/) on
[Twitter](http://twitter.com/tpope) and
[GitHub](https://github.com/tpope).

## License

Copyright (c) Tim Pope.  Distributed under the same terms as Vim itself.
See `:help license`.
