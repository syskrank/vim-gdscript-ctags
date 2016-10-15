#vim-gdscript-ctags

## About
This tiny project is dedicated to adding more GDScript support into the VIM editor via using ctags.

![Tagbar excuberant-ctags GDSCript demo](https://s17.postimg.org/ig7plkyfj/gdscript_tagbar_ctags.png)

Currently supported tags:
-------------------------

- constants
- export variables
- onready-constructions
- signals
- functions
- preloads


## Dependencies
It is highly recommended to use these settings with the following VIM plugins:

Tagbar:
-------
https://github.com/majutsushi/tagbar

GDScript syntax support:
------------------------
https://github.com/a-watson/vim-gdscript

## Installation

( also see ctags-excerpt and vimrc-excerpt files )

Add the following to your ~/.ctags file:
----------------------------------------

	--langdef=gdscript
	--langmap=gdscript:.gd

	--regex-gdscript=/^[ \t]*const[ \t]+([a-zA-Z0-9_]+)[ \t]*/\1/c,constant/i
	--regex-gdscript=/^[ \t]*export[ \t]*(\([ \t]*[a-zA-Z0-9_, \"\*\.]*\)|[ \t])+var[ \t]+([a-zA-Z0-9_]+)[ \t]*/\2/e,export/i
	--regex-gdscript=/^[ \t]*onready[ \t]+var[ \t]+([a-zA-Z0-9_]+)[ \t]*/\1/o,onready-variable/i
	--regex-gdscript=/^[ \t]*signal[ \t]+([a-zA-Z0-9_]+)[ \t]*/\1/s,signal/i
	--regex-gdscript=/^[ \t]*func[ \t]+([a-zA-Z0-9_]+)[ \t]*/\1/f,function/i
	--regex-gdscript=/^[ \t]*var[ \t]+([a-zA-Z0-9_]+)[ \t]=[ \t]*preload*/\1/p,preload/i

Add the following to your ~/.vimrc file:
----------------------------------------

```viml
let g:tagbar_type_gdscript = {
			\'ctagstype' :'gdscript',
			\'kinds':[
			\'c:constants',
			\'e:exports',
			\'o:onready',
			\'p:preloads',
			\'s:signals',
			\'f:functions',
			\]
			\}
```
