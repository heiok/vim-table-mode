# VIM Table Mode

An awesome automatic table creator & formatter allowing one to create neat
tables as you type.

## Change Log
See <a
href="https://github.com/dhruvasagar/vim-table-mode/blob/master/CHANGELOG.md">
CHANGELOG.md </a>

## Getting Started
### Installation

There are 2 ways to do this

1. I recommend installing <a
   href="https://github.com/tpope/vim-pathogen">pathogen.vim</a> and then
   adding a git submodule for your plugin:

   ```sh
$ cd ~/.vim
$ git submodule add git@github.com:dhruvasagar/vim-table-mode.git bundle/table-mode
   ```
2. Copy autoload/todomode.vim, plugin/todo-mode.vim, doc/todo-mode.txt to
   respective ~/.vim/autoload/, ~/.vim/plugin and ~/.vim/doc under UNIX or 
   vimfiles/autoload/, vimfiles/plugin/ and vimfiles/doc under WINDOWS and
   restart VIM

### Requirements

Depends on <a href="https://github.com/godlygeek/tabular">Tabular</a>. Make
sure Tabular is installed and loaded into your runtime to ensure this works.

### Usage

- On the fly table creation :

   By default the table column separator is '|' (it can be changed). As soon as
   you type it on a new line (ignores indentation) the script gets to work on
   creating a table around it. As you type and define more columns, the table
   is completed, formatted and aligned automatically on the fly.

   Since this could lead to unwanted behavior I have disabled table mode by
   default. You would have to use `:TableModeToggle` command or the table mode
   toggle mapping, which is `<Leader>tm` by default to toggle the table mode or
   you can directly use `:TableModeEnable` and `:TableModeDisable` to enable or
   disable the table mode. This is on a per buffer basis and so it does not
   cause any unusual behavior unless enabled explicitly. Please read `:h
   table-mode` for further information.

- Format existing content into a table :

   Table Mode wouldn't justify it's name if it didn't allow formatting
   existing content into a table. And it does as promised. Like table creation
   on the fly as you type, formatting existing content into a table is equally
   simple. You can visually select multiple lines and call `:Tableize` on it, or
   alternatively use the mapping `<Leader>T` (this is configurable). `:Tableize`
   accepts a range and so you can also call it by giving lines manually like
   `:line1,line2Tableize`, but this is not that intuitive. You can also use
   the mapping `<Leader>T` with a `[count]` to apply it to the next `[count]`
   lines in usual vim style.

- Move between cells :

   Now you can move between cells using table mode motions. Check `:h
   table-mode-motion-prefix` for more details.

- Manipulating Table :

  - Cell Text Object :

      Tableize provides a text object for manipulating table cells. By default
      it's `tc`, but that can be changed if you wish to by setting the
      `g:table_mode_cell_text_object` option.

      This is intelligent in the sense that if you use it to delete the
      contents it will delete everything till the `g:table_mode_separator` so
      that the cell is removed and you can enter new stuff if you wish to (had
      you used 'c' operator), having to input the `g:table_mode_separator`
      again to form the cell & realign it (since it can't be done from the
      text object itself). However if you were to 'y' or yank the text, it
      would copy the right text, i.e. the contents of the cell and nothing
      else.
  - Delete Row :

      You can use the `<Leader>tdd` mapping defined by the option
      `g:table_mode_delete_row_map` to delete the current table row (provided
      you are within a table row), this can be preceeded with a [count] to
      delete multiple rows just like you would with 'dd'.

  - Delete Column :

      You can use the `<Leader>tdc` mapping defined by the option
      `g:table_mode_delete_column_map` to delete the entire current column
      (provided you are within a table row), this can also be preceeded with a
      [count] to delete multiple columns.

### Demo

<a href="http://www.youtube.com/watch?v=sK2IH1hiDkw"><img
src="https://raw.github.com/dhruvasagar/vim-table-mode/master/youtube.png"/></a>

## Contributing

### Reporting an Issue :
- Use <a href="https://github.com/dhruvasagar/vim-table-mode/issues">Github
  Issue Tracker</a>

### Contributing to code :
- Fork it.
- Commit your changes and give your commit message some love.
- Push to your fork on github.
- Open a Pull Request.

## Credit
I must thank Tim Pope for inspiration. The initial concept was created by him
named <a href="https://gist.github.com/tpope/287147">cucumbertables.vim</a>.

Also a shout out to godlygeek who developed the incredible <a
href="http://github.com/godlygeek/tabular">Tabular</a> plugin which does most
of the grunt work behind the scenes.
