# grep --indent

## Patch to grep-2.20 to implement grep --indent

This patch modifies grep-2.20
to implement a new grep output format,
`grep --indent`.

With this option, the format of grep output is changed
so that each filename is printed just once,
on a line by itself, just before the first match.
Then, the rest of the information about each match
(line number or byte offset, matching text)
is printed with an indent, but not a repeat of the filename.

## Options

The `--indent` option has been added.

--indent=_n_

Indent _n_ spaces.

Default is 4 spaces.

## Why

I often run into the situation where,
although I do want the filename printed,
it can be a _really_ long pathname -- so long
that it can be hard to read the matching lines,
because they start so far to the right of each output line.

It can be like reading a newspaper column,
but with a pathname prepended to every line.
Or even worse.

I thought about just doing some sort of post-processor
to convert grep output to produce the indented format.
And, I have done that.  But the result is not satisfactory.
Grep can produce many output formats,
and there are many cases where it is difficult to tell
filename / line number / context separators from
some line that looks a lot like grep punctuation.

I even tried restricting grep to use some combination
-Z / -z to make the output unambiguous, but the logic
to post-process grep output is way more complicated
than just patching grep.

It is open source.  You can do that.

## Why grep 2.20

The latest (as of 2016-Jul-17) version of GNU grep is 2.25.
Why make a patch to version 2.20?

Because I am on Ubuntu 15.04,
and grep-2.20 is what I get when I run

```
    apt-get source --compile grep
```

When I upgrade my Linux box, I will update the patch.

## Thank you

Thank you Mike Haertel.

Thank you Free Software Foundation.

Thanks for the open source.

## License

The is a patch to GNU software.

It inherits the license of the source code to GNU grep 2.20.


This program is free software; you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as
published by the Free Software Foundation; either version 3 of the
License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

##

-- Guy Shaw

   gshaw@acm.org

