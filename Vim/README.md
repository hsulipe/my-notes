# Vim

## Objective

Make a little glossary of vim features and shortcuts.

## Modes 

- [Normal](#normal)
- [Insert](#insert)
- [Visual](#visual)
- [Replace](#replace)  
- [Command](#command)

### Normal

By default, Vim starts in “normal” mode. Normal mode can be accessed from other modes by pressing `Esc` or `Ctrl + c`.

### Insert

To enter insert mode you should press one of the following commands: 
- `i` - starts insert mode where the cursor is placed.
- `a` - moves the cursor to the **next character** and starts insert mode.
- `o` - inserts a new line **below the current line** and enters insert mode on the new line.
- `Shift + i` or `I` - moves the cursor to the **beginning of the line** and enters insert mode.
- `Shift + a` or `A` - moves the cursor to the **end of the line** and enters insert mode.
- `Shift + o` or `O` - inserts a new line **above the current line** and enters insert mode on the new line

### Visual

To enter visual mode you should press one of the following commands: 
- `v` - enter visual mode where the cursor is placed, and also starts a selections point.
- `Shift + v` or `V` - enters linewise-visual mode, this will make text selections by lines.
- `Ctrl + v` - enters blockvisual mode, this will make text selections by blocks; moving the cursor will make rectangle selections of the text.

### Replace

Press `Shitf + R` and it will enter replace mode. Now whatever you type will replace the existing text.

### Command

To enter command mode type ’:’ from normal mode and then type your command which should appear at the bottom of the window. `:%s/foo/bar/g`

Commands:  
- `%` Means across all lines.
- `s` Substitute.
- `/foo` is regex to find things to replace.
- `/bar/` is regex to replace things with.
- `/g` means global, otherwise it would only execute once per line.

## Writing multiple lines

1 - Press `Ctrl + v` to enter into visual block mode.  
2 - Use `↑ / ↓ / j / k` to select multiple lines.  
3 - Press `Shift + i` and start typing what you want.  
4 - After you press `Esc`, the text will be inserted into all the lines you selected.  

## Deleting multiple lines with block selection

1 - Press `Shift + v` to enter into visual block mode.  
2 - Use `↑ / ↓ / j / k` to select multiple lines.  
3 - Press `d` to delete the block selected.  

## Markers

## References
[Insert test into multiple lines at once](https://riptutorial.com/vim/example/7301/insert-text-into-multiple-lines-at-once)