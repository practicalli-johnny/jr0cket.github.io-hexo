title: "spacemacs - tips from an emacs driven developer"
tags:
---




# Contributing to Spacemacs

Join the Gitter.im channel and discuss your proposed change.

Review the issues on the Spacemacs Github repository

## Making a Pull Request

You can make a pull request by using magit and the Spacemacs Github repository

Open Magit using `M-m g s` or `SPC g s` then `b B` to create a new branch, choose develop as its root branch and then give it a name.

Edit the files that make up your changes, then open Magit status `SPC g s` and stage your changes by navigating to them and pressing `s`,

Commit your changes uisng `c c`.

Use `P` to push your change, make sure you `-u` to set upstream then `e` to push elsewhere. Choose the branch you just made and then the name of the remote that you have assigned to your fork at `git@github.com:geo7/spacemacs`. Then `P` to push it to your own fork.

Visit the Spacesmacs Github repository at https://github.com/syl20bnr/spacemacs in your browser and press the green pull request button to create a pull request with this specific change.

