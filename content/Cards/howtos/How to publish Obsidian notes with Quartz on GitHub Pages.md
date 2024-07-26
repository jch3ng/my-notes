
> [!NOTE]
> This is a stripped down version of Nicole van der Hoeven's [How to publish Obsidian notes with Quartz on GitHub Pages](https://notes.nicolevanderhoeven.com/How+to+publish+Obsidian+notes+with+Quartz+on+GitHub+Pages#Change+the+%60origin%60+remote)
> 

## Step 1. Install Quartz

```
npx quartz build --serve
```
you should see: 

```
Quartz v4.2.4 

(node:5441) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
(Use `node --trace-deprecation ...` to show where the warning was created)
Cleaned output directory `public` in 10ms
Found 1 input files from `content` in 13ms
Parsed 1 Markdown files in 78ms
Filtered out 0 files in 23μs
Emitted 11 files to `public` in 56ms
Done processing 1 files in 159ms
Started a Quartz server listening at http://localhost:8080
hint: exit with ctrl+c
[200] /
[200] /index.css
[200] /prescript.js
[200] /postscript.js
[200] /static/contentIndex.json
[200] /static/icon.png
[200] /static/icon.png
^C

```

Run http://localhost:8080

## Step 2. Setup GitHub repository


### Create a GitHub repository

in GitHub make a repository named `my-notes`.


### Change the `origin` remote


```
git remote -v
```

You should see something like:

```
origin  https://github.com/jackyzha0/quartz.git (fetch)
origin  https://github.com/jackyzha0/quartz.git (push)
upstream        https://github.com/jackyzha0/quartz.git (fetch)
upstream        https://github.com/jackyzha0/quartz.git (push)
```

which shows two remotes, `origin` and `upstream`, each of which has a `fetch` and a `push`.

Now run:
```
git remote rm origin
```

This command removes the `origin` remote.

Now add the remote back, but this time with the correct repository:

```
git remote add origin git@jch3ng.github.com:jch3ng/my-notes.git
```


### Sync your changes

In this section, you are pushing the changes you made to your local repository (`my-notes` on your computer) to your remote repository (`my-notes` on GitHub). Run:

```
npx quartz sync --no-pull
```


