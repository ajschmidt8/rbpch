# rbpch
Pre Commit Hook used for RB

Hey RB'ers,
I've been reading a lot about Git Hooks lately and trying to figure out if
there was a way to incorporate them into our workflow. If you're not familiar
with Git Hooks, you can read up on them [here](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks).

Basically, they're operations that are performed when certain git commands are
executed. In the case of this hook, any staged files are scanned for keywords
that shouldn't be committed (i.e. debug, log, ad, etc.). You can see an example
screenshot below:

![alt text](http://i.imgur.com/eFtWsAU.png)
