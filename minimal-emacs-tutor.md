# Minimal Emacs Tutorial

This tutorial is a smaller copy from the original *Emacs Tutor* .

I wrote it in this form by no reason. Hope you can enjoy this reading!

## Exit

> The first question a newbie asks when he starts with a new text editor is: *How do I exit the editor?*

| Command | Description       |
| ------- | ----------------- |
| C-z     | Run background    |
| C-x C-c | Kill (exit) Emacs |

## Moving around

> The second thing to do is moving instead of staring at the cursor.

Luckily, Emacs is easy-to-use. You can move around just pressing ↑ ↓ ← → .

But there is another way, *there is always another way...*

### Screen

| Command | Description            |
| ------- | ---------------------- |
| C-v     | Page down              |
| M-v     | Page up                |
| C-l     | Top/mid/bottom of page |

### Cursor

The control key is often bound with commands of lines / characters.

| Command | Description            |
| ------- | ---------------------- |
| C-f     | Forward                |
| C-b     | Backward               |
| C-n     | next line              |
| C-p     | Previous line          |
| C-a     | Beginning of   line    |
| C-e     | End of line            |

On the other hand, alt (or called META) is often related to commands of sentences / texts.

| Command | Description             |
| ------- | ----------------------- |
| M-a     | Beginning of   sentence |
| M-e     | End of sentence         |
| M-<     | Beginning of all   text |
| M->     | End of all text         |

## Files

> Now you want to do some real editing.

| Command | Description             |
| ------- | ----------------------- |
| C-x C-f | Find (open) a file      |
| C-x C-s | Save a file             |

```
NOTICE: 

- The origin file will be renamed by adding a suffix "~" after updated.
- Sometimes you might see "#\<filename\>#" files. They are saved by Emacs automatically. (We'll talk this later.)
```

## Buffers

Buffers are texts which are stored by the opening Emacs.

They are not necessarily a real file until you save them.

| Command | Description   |
| ------- | ------------- |
| C-x C-b | List buffers  |
| C-x b   | Switch buffer |
| C-x s   | Save buffer   |

## Editing

You can edit or delete by just type or \<DEL\>. It is the most common way on any OS.

There are also other commands.

<!-- TODO: Modern editors always provide us with "spells", so we can do less typing. -->

### Deletion

| Command   | Description               |
| --------- | ------------------------- |
| C-d       | Delete a   character      |
| M-d       | Kill next word            |
| M-\<DEL\> | Kill previous   word      |
| C-k       | Kill to end of   line     |
| M-k       | Kill to end of   sentence |

### Paste 

There is difference between "delete" and "kill". If you kill a word/sentence, you can "yank" (paste) it back.

| Command | Description        |
| --------| ------------------ |
| C-y     | Yank back          |
| M-y     | Yank previous kill |

### Completion

Emacs completes your typing by "remembering" what you have typed before. 

Press \<TAB\> for completing.

### Undo

There are three ways to undo a change in the text.

| Command | Description      |
| --------| ---------------- |
| C-/     | Undo text change |
| C-_     |                  |
| C-x u   |                  |

## Searching

| Command | Description      |
| --------| ---------------- |
| C-s     | Forward search   |
| C-r     | Reverse search   |

Emacs search is "incremental", which means search happens while you're typing.

After you finish typing,

| Command    | Description                   |
| ---------- | ----------------------------- |
| C-s        | Jump to next   occurrence     |
| C-r        | Jump to previous   occurrence |
| \<DEL\>    | Jump back                     |
| \<RETURN\> | Terminate search              |

## Command

Emacs is smart. You can "tell" it to do things.

### Extension

We do use commands in previous sections. Now take a look at how they work.

| Command    | Description                      |
| ---------- | -------------------------------- |
| C-x        | Extends character   command      |
| M-x        | Extends named command (function) |

```
NOTICE: The function ``previous-line`` refers to the command ``C-p`` .
```

For example, one of the most frequently used command.

| Command                                    | Description    |
| ------------------------------------------ | -------------- |
| M-x   replace-string   <former>   <latter> | Replace string |

### Repeat

| Command           | Description                      |
| ----------------- | -------------------------------- |
| C-u 8   <command> | Repeat   <command> 8 times       |
| C-u 8 C-v         | Down 8 lines                     |
| C-u 8 M-v         | Up 8 lines                       |

### Disabled Commands

Some commands are "disabled" to avoid being used accidentally by newbies.

**For now, just type ``n`` when you come across one.**

## Surface

### Frames

Frames contains menus, scroll bars, echo areas, etc.

```
NOTICE: People may call the object "windows" which refer to "frames" here.
```

| Command          | Description    |
| ---------------- | -------------- |
| M-x make-frame   | Make a frame   |
| M-x delete-frame | Delete a frame |

### Windows

Emacs can have several "windows" (i.e. help window).

| Command   | Description                                       |
| --------- | ------------------------------------------------- |
| C-x 1     | Exist others and   stay at the current window     |
| C-x 2     | Generate a   horizontal window with the same text |
| C-x 4 C-f | Open a file in a   vertical window                |

 When you have two windows.

| Command |  Description                    |
| ------- | ------------------------------- |
| C-x o   | Switch to   "other" window      |
| C-M-v   | Scroll down the   other windows |

<!-- TODO: Directories and file navigation. -->

### Echo Area

It's at the bottom that shows commands you typed. 

### Mode Line

It's just above echo area that tells useful information about Emacs and text status.

```
-:**-  TUTORIAL       63% L749    (Fundamental)
```

 Let's take a look at them!

> ``**`` means the text is changed
>
> ``TUTORIAL`` is the current buffer
>
> ``63%`` indicates the current position
>
> ``L749`` shows how many lines the text contains
>
> ``(Fundamental)`` means the in which mode you are using Emacs

## Modes

**Major modes are modes that can be used one at a time.**

| Command           | Description |
| ----------------- | ----------- |
| M-x   <mode-name> | Switch mode |

Minor modes are different -- **you can use any numbers of minor mode under any major mode. **

| Command              | Description                   |
| -------------------- | ----------------------------- |
| M-x   auto-fill-mode | Good for   human-text editing |

## Hold on a Second

There are few things mentioned in the *Emacs Tutor* I haven't covered yet.

### Recursive Editing Level 

If the mode line shows ``[(Fundamental)]`` instead of ``(Fundamental)`` , then you're in the recursive editing level.

Type 3 \<ESC\> to get out.

## Getting Help

| Command            | Description                                   |
| ------------------ | --------------------------------------------- |
| C-h                | Help                                          |
| C-h ?              | If you're really   lost                       |
| M-x help           |                                               |
| C-h c   <command>  | Brief description   of a command              |
| C-h k   <command>  | Full document of   a command                  |
| C-h f   <function> | Full document of   a function                 |
| C-h v   <variable> | Document of   variable                        |
| C-h a   <apropos>  | List all (named)   commands with that keyword |
| C-h I   <info>     | Manuals                                       |

## Getting More Help

Please read *Emacs Manuals* (By ``C-h I m emacs`` or ``C-h r``) and enjoy yourself!!!
