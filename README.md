# Sweep36

For more info abot the origin of this keyboard see the [original readme](keyboards/sweep36/readme.md).

This document is meant to describe operational tasks in an easy workflow.
Of course if yo know what you're doin wit git, feel free to chagne the procedure how you see fit.

## Prerequisites

This procedure assumes you have a working qmk setup on your machine. See [upstream docs](https://docs.qmk.fm/#/newbs_getting_started?id=setting-up-your-qmk-environment) if that's not the case.

## First time setup

After checking out this repo, you'll need to add 2 remotes:

* `git remote add qmk_upstream https://github.com/qmk/qmk_firmware.git`
* `git remote add miryoku_qmk https://github.com/manna-harbour/miryoku_qmk.git`

## Building the firmware

The idea of this procedure is to create a temporary/disposable branch so that each time you do this you start wit a fresh, updated version of the upstream firmware.

As you might have noticed, this uses the [Miryoku](https://github.com/manna-harbour/miryoku) layout.

```bash
git checkout -d miryoku_qmk/miryoku # checkout in detached mode, it's all temporary
git revert --no-edit `git log --grep='^\[miryoku-github\]' --pretty='format:%H' | tr '\n' ' '` # see original docs
git merge -m 'merge qmk upstream' qmk_upstream/master
git checkout sweep36 -- keyboards/sweep36/
make git-submodules
make sweep36:manna-harbour_miryoku -e MIRYOKU_ALPHAS=QWERTY # just an example
```

You can find all variables/options for Miryoku in the [reference manual](https://github.com/manna-harbour/miryoku/tree/master/docs/reference).

At this point you can iterate on building with different keymaps options.

## Flashing the firmware

To flash the produced .hex file you can use [QMK Toolbox](https://github.com/qmk/qmk_toolbox) (if you prefer GUIs) or you can repeat the last make target addin `:dfu` to the target (all options need to be repeated as well).

Given the example above, this would be:

```bash
make sweep36:manna-harbour_miryoku:dfu -e MIRYOKU_ALPHAS=QWERTY
```

## Cleaning up

To cleanup you need to check out the original branch, remove untracked files and garbage collect:

```bash
git checkout sweep36
git clean -xfdf # yes, -f twice
git gc
```
