[user]
	name = Dan Lofquist
	email = dan.lofquist@input-consulting.se
[core]
	excludesfile = /Users/Dan/.gitignore_global
[difftool "sourcetree"]
	cmd = opendiff \"$LOCAL\" \"$REMOTE\"
	path = 
[mergetool "sourcetree"]
	cmd = /Applications/SourceTree.app/Contents/Resources/opendiff-w.sh \"$LOCAL\" \"$REMOTE\" -ancestor \"$BASE\" -merge \"$MERGED\"
	trustExitCode = true

# color {{{
[color]
    branch = auto
    diff = auto
    status = auto

[color "branch"]
    current = red reverse
    local = blue
    remote = green

[color "diff"]
    meta = yellow bold
    frag = magenta bold
    old = red bold
    new = green bold

[color "status"]
    added = yellow
    changed = green
    untracked = cyan

# }}}
# push/pull/diff/options {{{
[push]
    default = tracking
[pull]
    default = current
[diff]
  memonicprefix = true
[branch]
  autosetuprebase = always
[apply]
  whitespace = nowarn

#}}}
# difftools {{{
[difftool "sourcetree"]
	cmd = opendiff \"$LOCAL\" \"$REMOTE\"
	path = 
[mergetool "sourcetree"]
	cmd = /Applications/SourceTree.app/Contents/Resources/opendiff-w.sh \"$LOCAL\" \"$REMOTE\" -ancestor \"$BASE\" -merge \"$MERGED\"
	trustExitCode = true

# }}}
# alias {{{
[alias]
    st = status -s

    cl = clone

    ci = commit
    cm = commit -m
    cma = commit -a -m
    ca = commit --amend
    amend = commit --amend
    caa = commit -a --amend -C HEAD
    filelog = log -u
    fl = log -u

    ai = add --interactive

    co = checkout
    br = branch 
    #"!git branch -ra | grep -v done"
    bra = branch -ra
    #list commands
    le = log --oneline --decorate
    ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
    ls = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate
    lds = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short
    ld = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=relative
    lc  = "!f() { git ll "$1"^.."$1"; }; f"
    lnc = log --pretty=format:"%h\\ %s\\ [%cn]"
    #list all aliases
    la = "!git config -l | grep alias | cut -c 7-"
    diff = diff --word-diff
    d = diff --word-diff
    dc = diff --cached
    #list modified files in last commit
    dl = "!git ll -1"
    #diff last commit
    dlc = diff --cached HEAD^
    dr  = "!f() { git diff "$1"^.."$1"; }; f"
    diffr  = "!f() { git diff "$1"^.."$1"; }; f"
    branch = branch -ra

    #reset commands
    r = reset
    r1 = reset HEAD^
    r2 = reset HEAD^^
    rh = reset --hard
    rh1 = reset HEAD^ --hard
    rh2 = reset HEAD^^ --hard

    #git svn
    svnr = svn rebase
    svnd = svn dcommit
    svnl = svn log --oneline --show-commit

    #stash
    sl = stash list
    sa = stash apply
    ss = stash save

    cp = cherry-pick
    grep = grep -Ii
    gr = grep -Ii
    #grep from root folder
    gra = "!f() { A=$(pwd) && TOPLEVEL=$(git rev-parse --show-toplevel) && cd $TOPLEVEL && git grep --full-name -In $1 | xargs -I{} echo $TOPLEVEL/{} && cd $A; }; f"

    #grep on filename
    f = "!git ls-files | grep -i"

    #rename branch tree to done-
    done = "!f() { git branch | grep "$1" | cut -c 3- | grep -v done | xargs -I{} git branch -m {} done-{}; }; f"

    #assume aliases
    assume = update-index --assume-unchanged
    unassume = update-index --no-assume-unchanged
    #show assumed files
    assumed = "!git ls-files -v | grep ^h | cut -c 3-"
    #unassume all the assumed files
    unassumeall = "!git assumed | xargs git update-index --no-assume-unchanged"
    assumeall = "!git st -s | awk {'print $2'} | xargs git assume"

    lasttag = describe --tags --abbrev=0
    lt = describe --tags --abbrev=0

    #merges
    ours = "!f() { git co --ours $@ && git add $@; }; f"
    theirs = "!f() { git co --theirs $@ && git add $@; }; f"
# }}}