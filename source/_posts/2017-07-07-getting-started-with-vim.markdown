---
layout: post
title: "Getting started with VIM"
date: 2017-07-07 02:44:24 +0530
comments: true
categories:
---

I don't think anyone who is reading this doesn't know about VIM. Everyone, one in their life has been forced to exit it. I have tried learning VIM a number of times but failed. I fumbled with it and pressed random keys to just get out of it. Most of times it has been because of my inability to select large blocks of text using mouse and deleting it, which I have been used to when using Atom and Sublime Text or some IDE. Using VIM requires you to be already comfortable with writing commands, i.e. you should be good at using command line. When you get comfortable with the keyboard only then can you master VIM. And that is one of the advantages of VIM, it forces you to minimize the use of mouse. Now not using mouse does 2 things, lets your hand sit on the keyboard and save the time for shifting to the mouse from the keyboard.

#### Why VIM?

VIM is available by default on most of the OS distributions. Also as one of my friend suggests you can use it to edit files on a remote hosts too. But that is not all. VIM's plugins are what makes it so great, just like any of the new editors out there VIM also has plugins support (20+ years old, meh!). Being old and a prefered choice of power users the number of plugins it has are around double that of Atom.

It has different modes, a few of which are Normal mode, Visual Mode, Insert Mode, Command Mode etc.. These can be invoked using different keys in the Normal mode that is given at start of VIM. These modes provide different kinds of functions. Command mode, as the name suggests, can be used to execute commands that can run on the current file. You can also add custom commands by yourself or by adding plugins. For example using a `:py` command to execute python code from VIM.

To make up for the mouse it has motions, in the normal mode you can use `h`, `j`, `k`, `l` to move the cursor left, down, up, right respectively. Prefix it with a number like `9k` can cause that counts of motion in the respective direction. There are many such motions like `H`, `G` etc. that are used to jump to top or bottom of the page. In Visual mode using these motions causes the text to get selected. Hence you can use complex combinations of these motions to select desired text and copy or replace it.

There are also similar text objects that are independent of the cursor position inside the scope. These work on the complete word, sentence, paragraph despite their position inside it. Ex - `diw` would delete a word while `dw` will delete only the part of the word after the prompt.
Similarly exists `daw`, `dis`, `das`, `dip`, `dap` etc..

These text-objects and motions enables a user to move faster and precisely without removing their hands from the keyboard and hence saving time.

I am beginning to use these motions and text to speed up the editing process.
