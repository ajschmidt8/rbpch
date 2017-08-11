# RB Pre-Commit Hook (rbpch)

Hey RB'ers,<br>
I've been reading a lot about Git Hooks lately and trying to figure out if
there was a way to incorporate them into our workflow. If you're not familiar
with Git Hooks, you can read up on them [here](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks).

Basically, they're operations that are performed when certain git commands are
executed. In the case of this `pre-commit` hook, any staged files are scanned for keywords
that shouldn't be committed (i.e. debug, log, ad, etc.). You can see an example
screenshot below:

Bad Keywords Found<br>
![alt text](http://i.imgur.com/eFtWsAU.png)

No Keywords Found<br>
![alt text](http://i.imgur.com/lElqb50.png)

# Global Installation
(borrowed from [here](https://coderwall.com/p/jp7d5q/create-a-global-git-commit-hook))

1. **Enable global git templates:**<br>
`git config --global init.templatedir '~/.git-templates'`<br>
This tells git to copy everything in ~/.git-templates to your per-project .git/ directory when you run git init

2. **Create a directory to hold the global hooks:**<br>
`mkdir -p ~/.git-templates/hooks`

3. **Clone this repo into global hooks folder:**<br>
`git clone git@github.com:ajschmidt8/rbpch.git ~/.git-templates/hooks`

4. **Make sure the hook is executable:**<br>
`chmod a+x ~/.git-templates/hooks/pre-commit`

5. **Re-initialize git in each existing repo you'd like to use this in:**<br>
`git init`<br>

# Per Repo Installation
1. **Clone this repo into hooks folder:**<br>
`git clone git@github.com:ajschmidt8/rbpch.git REPO/.git/hooks`

2. **Make sure the hook is executable:**<br>
`chmod a+x REPO/.git/hooks/pre-commit`

# Uninstall
1. **Remove `pre-commit` from hooks folder:**<br>
`rm ~/.git-templates/hooks/pre-commit`<br>
or<br>
`rm REPO/.git/hooks/pre-commit`

# FAQs
* **Can I bypass the pre-commit hook?**<br>
Yup! Just use the `--no-verify` flag (`-n` for short). (i.e. `gmsg 'your awesome commit message' -n`)

* **Is the `pre-commit` file pushed to the remote repo with the other staged files?**<br>
Nope! ([source](https://stackoverflow.com/questions/12222186/are-git-hooks-pushed-to-the-remote-when-i-git-push))

* **Will running `git init` in an existing repo cause any issues?**<br>
Nope! <br>
"Running git init in an existing repository is safe. It will not overwrite things that are already there. The primary reason for rerunning git init is to pick up newly added templates" ([source](https://git-scm.com/docs/git-init))

* **Does this hook scan *ALL* staged files?**<br>
Nope! Only the following file extensions are scanned: `.php, .html, .js`. Feel free to Slack me or submit a PR if you want to add more.

* **What keywords are checked?**<br>
As of right now, the following keywords are scanned:<br>
    * `var_dump(`
    * `die(`
    * `print_r(`
    * `debug_print_var`
    * `console.debug(`
    * `console.info(`
    * `console.log(`
    * `console.warn(`
    * `ad`
    
Feel free to Slack me or submit a PR if you want to add more.

---
[Source](https://github.com/borisguery/git-keywords-checker) for original pre-commit bash script. 
