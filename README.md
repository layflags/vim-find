# Find files in subdirectories #

by Vladimir Marek 2006
Version 6.0

<http://vim.wikia.com/wiki/Find_files_in_subdirectories>

--------------------------------------------------------

I'm working with big, nested workspaces and often I don't remember the exact path to the file, only its filename or part of the filename. If I know some of the text *in* the file, I could always recursively use 'vimgrep', but for searching on filenames alone I have been using:

	:!find . -name ...

to locate the file and then edit it. I was trying to find if there is some solution directly in Vim, and haven't found one. Closest were `:find` and `:globpath()`. `:find` works nearly as I need, but unfortunatelly it opens the first file of a given name without telling me that there are more. For `globpath()` I was unable to make it work with the `**` construction, so that it would look into all subdirectories under current directory.
So I wrote this small function. You can use it like this:

	:Find whatever.c - this opens the file "src/core/whatever.c"

If there is more than one match, it will present you a selection:

	:Find Makefile
	1 ./src/Makefile
	2 ./src/core/Makefile
	3 ./src/api/Makefile
	...
	89 ./src/deelply/hidden/Makefile
	90 ./Makefile
	Which ? (CR=nothing)

You may also use wildchars (whatever find(1) knows).

	:Find *stream*.c
	1 ./src/core/i_stream.c
	2 ./src/core/o_stream.c
	3 ./src/core/streamio.c
	Which ? (CR=nothing)

...

Read the [full article here](http://vim.wikia.com/wiki/Find_files_in_subdirectories)!

