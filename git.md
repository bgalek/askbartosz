# git

## Set global .gitignore <a href="#set-global-gitignore" id="set-global-gitignore"></a>

Never add your system specific files to repository git ignore. Why every project needs to have .DS\_Store? Will you change it to Thumbs.db after moving to Windows?

Create `.gitignore` file in your home folder with example content:

```gitignore
*~
.DS_Store
*.iml
.idea
/out/
```

and set your git config

`git config --global core.excludesfile '~/.gitignore'`

## Committer for your work projects other for opensource projects <a href="#committer-for-all-company-projects-other-for-opensource-projects" id="committer-for-all-company-projects-other-for-opensource-projects"></a>

You can set git config based on directory structure.

Consider two directories `/home/bgalek/opensource` and `/home/bgalek/work`

I want to commit company's repositories using my @company.com email but opensource github projects using my (default) private email.

Create additional git-config file (i.e. `~/.gitconfig-work`)

```toml
[user]
    name = Bartosz Galek
    email = bgalek@company.com
```

and simply conditionally add it to your main `~/.gitconfig` file

```toml
[includeIf "gitdir:~/work/**"]
    path = .gitconfig-work
```

This setup will work for any repository inside `work` directory.

## Merging "drugs" with "alcohol" <a href="#merging-drugs-with-alcohol" id="merging-drugs-with-alcohol"></a>

Sometimes you need to merge `drug` branch to `alcohol` repository. Remember that you can do it only if `drug` is forked from `Ibuprofen`. Watch out for `Paracetamol` origin - it has security issues with `alcohol`.
