# AIX2 Reality (BattleField 2 mod)

[**FAQ and downloads**](https://vk.com/@-161984294-english-faq)

This repository contains the latest patch for BF2 mod aix2_reality version 4.93.

If you do not have the mod or the patch, please visit the provided downloads link.
This repository is for those who already have the patch and want to update it with downloading only the changed files.

Got a problem? Refer to [issues](https://github.com/lastnightmare/aix2_reality/issues) or create a new one.

## How to update to the latest patch?

Make sure you have [Git [48 MB]](https://git-scm.com/download/win) and [Git LFS [8 MB]](https://git-lfs.github.com/) installed.
I suggest opting out Git GUI during Git installation, but Git Bash is strongly advised.

The default BF2 mods folder (`C:\Program Files (x86)\EA Games\Battlefield 2\mods\`) is a system directory and one needs to have administrative privileges to make changes under Program Files.
Therefore, you need to put your previous files in a separate folder in a user directory.
*It is better if you put only patch files*, otherwise you can copy the entire `aix2_reality` folder but it will take more time later.

Download [`.gitattributes`](https://raw.githubusercontent.com/lastnightmare/aix2_reality/master/.gitattributes) and put it near the other files.
You should have the following folder structure:

```
aix2_reality
│   .gitattributes
│   common_server.zip
│   effects_server.zip
│   menu_server.zip
│   mod.desc
│   New_weapons_server.zip
│   Objects_client.zip
│   objects_server.zip
│
├───ai
├───Levels
├───Objects
└───python
```

### The commands

Open a terminal and change directory to `aix2_reality` described above.

    $ git init
    $ git lfs install --local
      # make sure you have .gitattributes
    $ git add .
      # you need to set your name and email once
      # git will throw an error when committing without this configuration
    $ git config user.name "Your Name"
    $ git config user.email "youremail@yourdomain.com"
    $ git commit -m "previous state"
    $ git remote add origin https://github.com/lastnightmare/aix2_reality
    $ git pull origin master --allow-unrelated-histories -X theirs

### Commands explained

    $ git init

Initialize hidden `.git` folder that is used by Git.

    $ git lfs install --local

Set up hooks for Gir Large File Support.
Git LFS looks for `.gitattributes` to see which files will be treated as large binary files.

    $ git add .

Add all files in this folder to be committed.
*This command will probably take a long time depending on the size of the changes.*
You can check which files are changed, and which are added for the commit by `$ git status`.
In case you want to add not all the files but some of them, use `add something` instead of this folder (`add .`).

    $ git config user.name "Your Name"
    $ git config user.email "youremail@yourdomain.com"

These configurations are necessary only because we will commit changes, and Git requires a name and an email for this operation.
Since you will not publish (i.e. `push`) the changes, they can be gibberish.
You can use `--global` flag to set your credentials for all repositories as Git suggest.

    $ git commit -m "previous state"

Commit (i.e. save and sign) the changes. The `-m` flag is to add a description without opening an editor.

    $ git remote add origin https://github.com/lastnightmare/aix2_reality

Provide the remote address for pull and push operations.
You can always pull from a public repository, but you need to have access for pushing.
If you want to contribute, see the corresponding section.

    $ git pull origin master --allow-unrelated-histories -X theirs

Get the changes from remote address `origin`, which is set this repository.
In case of conflicting files, prefer this repository.
You will be prompted for the description of merge commit. Simply save and close the editor.

---

You can keep this folder to get the possible future changes.
Since you have already set up everything, call only `pull` next time.

> `$ git pull origin master --allow-unrelated-histories -X theirs`

Use `$ git log` to confirm you have successfully pulled and merged the changes.

Use `$ git lfs pull` to make sure the binary files are in not cached but in their original format.
They should already be correct if you followed the instructions carefully (added `.gitattributes` along with other files before the commit).

Use `$ git reset --hard` to return to the last committed state. **It will delete any other changes.**

Use `$ git diff --name-status HEAD~1 origin/master` to compare which files are changed from the previous commit (`HEAD~1`) to the remote repository `origin`, or any other combination (`HEAD`, `HEAD~2`, etc.).

As noted under the description of `git add`, use `$ git status` all times.

## Contributing

If you want to update the patch, fork this repository and clone yours.

Set up Git LFS.

> `$ git lfs install`

Make sure you do not change the line endings.

    $ git config core.autocrlf false

Make your changes and push from local.

    $ git add .
    $ git commit
    $ git push

Create a pull request.
