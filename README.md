# oh-my-zsh git plugin

This plugin is a complete replacement for the default oh-my-zsh git plugin, and provides quite a few useful
aliases and functions. The motivation to replace the default plugin stems from the fact that it comes with
some inconsistencies that make a few popular commands rather unintuitive:

- `gcm='git checkout master'`: this is inconsistent with `gco='git checkout'`,  
  and on top of that it steals what should be the shortcut for `git commit -m`.
- Similar issues with `git log`: half of the commands use `glg`, the other half `gl`,  
  but `gl` by itself is `git pull` (!?), for which `gpl` would make more sense.
- ...

The efficiency of these shortcuts is kind of lost when you have to remember different letters for the same
subcommand depending on the parameter(s) you're using ...

In this plugin, great care care is taken to make sure all aliases are the most intuitive they can possibly
be.  
On top of that, quite a few extra functions are added.

## Installation

To use this plugin, clone this repo to `~/.oh-my-zsh/custom/plugins`:

```
git clone https://github.com/davidde/git.git ~/.oh-my-zsh/custom/plugins/git
```

This will automatically override the default git plugin.

If you aren't yet using the default plugin, add `git` to the plugins in your `~/.zshrc` file:

```
plugins=(git)
```

## Aliases cheatsheet

| Alias         | Command                                                   |
| :------------ | :-------------------------------------------------------- |
| **g**         | git                                                       |
| **galias**    | git_list_aliases'                                         |
| **ga**        | git add'                                                  |
| **gaa**       | git add --all'                                            |
| **gam**       | git commit --amend -m'                                    |
| **gama**      | git commit --amend -am'                                   |
| **gb**        | git branch'                                               |
| **gba**       | git branch --all \| cat'                                  |
| **gbr**       | git branch --remotes \| cat'                              |
| **gbd**       | git branch --delete'                                      |
| **gbdf**      | git branch --delete --force'                              |
| **gbls**      | git branch --list \| cat'                                 |
| **gbl**       | git blame'                                                |
| **gbll**      | git_blame_line _\<file> [\<from line>] [\<to line>]_'     |
| **gbs**       | git bisect'                                               |
| **gbsb**      | git bisect bad'                                           |
| **gbsg**      | git bisect good'                                          |
| **gbsr**      | git bisect reset'                                         |
| **gbss**      | git bisect start'                                         |
| **gc**        | git commit --verbose'                                     |
| **gcm**       | git commit -m'                                            |
| **gcmg**      | git commit --gpg-sign -m'                                 |
| **gcms**      | git commit --signoff -m'                                  |
| **gcma**      | git commit -ma'                                           |
| **gcmae**     | git commit --allow-empty-message -ma ""'                  |
| **gcmag**     | git commit --gpg-sign -ma'                                |
| **gcmas**     | git commit --signoff -ma'                                 |
| **gcmau**     | git commit -ma "Update"'                                  |
| **gcme**      | git commit --allow-empty -m'                              |
| **gcf**       | git config'                                               |
| **gcfls**     | git config --list \| cat'                                 |
| **gcl**       | git clone'                                                |
| **gclrs**     | git clone --recurse-submodules'                           |
| **gclcd**     | git_clone_and_cd'                                         |
| **gcnt**      | git_count'                                                |
| **gcnta**     | git_count_all'                                            |
| **gco**       | git checkout'                                             |
| **gcob**      | git checkout -b'                                          |
| **gcobb**     | git checkout -'                                           |
| **gcom**      | git checkout $(git_main_branch)'                          |
| **gcod**      | git checkout develop'                                     |
| **gcoc**      | git_checkout_child'                                       |
| **gcop**      | git_checkout_parent'                                      |
| **gcp**       | git cherry-pick'                                          |
| **gcpa**      | git cherry-pick --abort'                                  |
| **gcpc**      | git cherry-pick --continue'                               |
| **gd**        | git diff'                                                 |
| **gds**       | git diff --staged'                                        |
| **gdst**      | git diff stash@{0}'                                       |
| **gdsth**     | git diff stash@{0} HEAD'                                  |
| **gdstp**     | git diff stash@{0}^ stash@{0}'                            |
| **gf**        | git fetch'                                                |
| **gfo**       | git fetch origin'                                         |
| **ggb**       | git log --graph --all --simplify-by-decoration'           |
| **gignore**   | git update-index --skip-worktree'                         |
| **gunignore** | git update-index --no-skip-worktree'                      |
| **gignored**  | git ls-files -v \| grep ^S'                               |
| **gl**        | glog --name-status'                                       |
| **glf**       | git_log_file _\<file> [\<from line>] [\<to line>]_ '      |
| **glg**       | glog --graph'                                             |
| **glgo**      | git log --graph --oneline'                                |
| **glgs**      | glog --graph --stat'                                      |
| **glo**       | git log --oneline'                                        |
| **gloc**      | git_locate_string _\<Line-of-Code> [\<file>]_'            |
| **glog**      | git log'                                                  |
| **glr**       | glog --reverse --name-status'                             |
| **gm**        | git merge'                                                |
| **gmom**      | git merge origin/$(git_main_branch)'                      |
| **gmum**      | git merge upstream/$(git_main_branch)'                    |
| **gmv**       | git mv'                                                   |
| **gp**        | git push'                                                 |
| **gpd**       | git push --delete'                                        |
| **gpdo**      | git push --delete origin'                                 |
| **gpf**       | git push --force-with-lease'                              |
| **gpl**       | git pull'                                                 |
| **gplr**      | git pull --rebase'                                        |
| **gplrm**     | git pull origin master --rebase'                          |
| **gplrs**     | git pull --recurse-submodules'                            |
| **gr**        | git reset'                                                |
| **grm**       | git reset --mixed'                                        |
| **grh**       | git reset --hard'                                         |
| **grk**       | git reset --keep'                                         |
| **grs**       | git reset --soft'                                         |
| **grhm**      | git_reset_head --mixed'                                   |
| **grhh**      | git_reset_head --hard'                                    |
| **grhk**      | git_reset_head --keep'                                    |
| **grhs**      | git_reset_head --soft'                                    |
| **grb**       | git rebase'                                               |
| **grba**      | git rebase --abort'                                       |
| **grbc**      | git rebase --continue'                                    |
| **grbm**      | git rebase $(git_main_branch)'                            |
| **grm**       | git remote'                                               |
| **grma**      | git remote add'                                           |
| **grmrm**     | git remote rm'                                            |
| **grmsu**     | git remote set-url'                                       |
| **grmsh**     | git remote show'                                          |
| **grmv**      | git remote -v'                                            |
| **grl**       | git reflog'                                               |
| **gs**        | git status'                                               |
| **gsh**       | git show'                                                 |
| **gshsf**     | git_show_stash_file _\<file> [\<stash number>]_'          |
| **gss**       | git_status_short'                                         |
| **gst**       | git stash'                                                |
| **gsta**      | git stash apply'                                          |
| **gstd**      | git stash drop'                                           |
| **gstl**      | git stash list'                                           |
| **gstls**     | git stash list \| cat'                                    |
| **gstp**      | git stash push'                                           |
| **gstpop**    | git stash pop'                                            |
| **gstsl**     | git stash show -l'                                        |
| **gstsp**     | git stash show -p'                                        |
| **gsub**      | git submodule'                                            |
| **gsuba**     | git submodule add'                                        |
| **gsubi**     | git submodule update --init'                              |
| **gsubpl**    | git submodule foreach git pull'                           |
| **gsubplom**  | git submodule foreach git pull origin $(git_main_branch)' |
| **gsubs**     | git submodule status'                                     |
| **gsubu**     | git submodule update --remote --merge'                    |
| **gt**        | git tag'                                                  |
| **gtma**      | git tag -ma'                                              |
| **gtms**      | git tag -ms'                                              |
| **gtd**       | git tag --delete'                                         |
| **gtls**      | git tag --list \| cat'                                    |
| **gwch**      | git whatchanged -p'                                       |
&nbsp;

---

> :warning: **Note:**
>
> This cheatsheet is optimized for memorability, and may not correspond literally with the actual aliases.
> E.g.:
>
> - "git graph branches"
> - `git log` commands are actually more verbose for nicer output.
> - `git commit -m --gpg-sign` has its flags switched because `-m` needs to be last.
> - Etc.
>
> Check out all commands with usage and clarifications in your local [git.plugin.zsh](./git.plugin.zsh) or the
> [repo's source code](https://github.com/davidde/git/blob/master/git.plugin.zsh).
>
> Alternatively, run `alias` to see _all_ alias implementations, or `galias` for this cheatsheet.  
> If you want to see any specific implementation, simply run `which <alias/function>`.

---
