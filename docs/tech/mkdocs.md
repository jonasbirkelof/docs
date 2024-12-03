---
title: MkDocs
---

If you want to develop a MkDocs site locally, you need to install some dependencies first: Ruby, Python and Pip. This page will explain how to install these dependencies and then how to install MkDocs. 

!!! warning

	Do not follow the instructions on the MkDocs page! Instead, follow the instructions for installing Jekyll on Windows. The Jekyll site offers an easier way of accomplishing just about the same thing as the MkDocs site.

## Material for MkDocs

While you *can* use "vanilla" MkDocs for documentation, it's much recommended that you use [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) instead as this is a really good MkDocs theme that will make a much better site and user experience. If you do, you don't need to proceed with this guide. Use my [Material for MkDocs](./material-for-mkdocs.md) guide for instructions on installation and basic configuration.

## Resources

- [MkDocs Documentation](https://www.mkdocs.org/user-guide/installation/)

## Prerequisites

Before you can install MkDocs you have to install Python, Pip and Ruby+Devkit.

### Python and Pip

Follow [this guide](./python.md) for instructions on how to install Python and Pip.

### Ruby+Devkit

<div class="steps" markdown>

1. Download Ruby+Devkit from [RubyInstaller Downloads](https://rubyinstaller.org/downloads/).

1. Run the installation file and follow the instructions. Use default options.

	!!! warning "Important"

		On the last stage of the installation wizard, run the **ridk install** step. This is needed for installing gems with native extensions. You can find additional information regarding this in the [RubyInstaller Documentation](https://github.com/oneclick/rubyinstaller2#using-the-installer-on-a-target-system).
		
		Select `MSYS2 and MINGW development tool chain`.

1. Open a new command prompt window from the start menu, so that changes to the `PATH` environment variable becomes effective

1. Install Jekyll and Bundler.
	
	```bash
	gem install jekyll bundler
	```

1. Check if Jekyll has been installed properly.

	```bash
	jekyll -v
	```

</div>

!!! info
	You may receive an error when checking if Jekyll has not been installed properly. Reboot your system and run `jekyll -v` again. If the error persists, please open a [RubyInstaller issue](https://github.com/oneclick/rubyinstaller2/issues/new).

## Install MkDocs

Install MkDocs globally:

```bash
pip install mkdocs
```

Check that MkDocs has been installed:

```bash
mkdocs --version
```