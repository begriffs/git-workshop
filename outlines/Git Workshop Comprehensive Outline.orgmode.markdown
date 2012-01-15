Git Foundations

# [#C] Class Description
* Distributed version control is all the rage these days, but is it worth it? It has been transformative for the dozens of organizations and thousands of developers that I've mentored on the unique implementation called Git. But don't take my word for it. Discover the joy of a version control system that works for you, not against you, in a hands-on workshop. Bring a Windows, Mac, or Linux laptop and we'll install, set up, use and bend Git into workflows that weren't even possible with the version control systems of yesteryear. Be prepared to rethink how lightweight, fast, and refreshing source code control can be. After completing this workshop you'll be able to do practical work with Git for your day job or weekend OSS hobby.

# [#A] Repo URLs, Links, Setup
* Workshop Materials
    * https://github.com/matthewmccullough/git-workshop
* Sample Project
    * https://github.com/matthewmccullough/hellogitworld
* Shell Scripts
    * https://github.com/matthewmccullough/scripts
* Shell Decorations
    * https://github.com/matthewmccullough/MatthewsShellConfig
* Cheat Sheet
    * http://refcardz.dzone.com/refcardz/getting-started-git
* GitHubStudents Temp Account
    * `git clone https://githubstudents:students987@github.com/githubstudents/hellogitworld.git`
* Created a Gist for Notes
    * https://gist.github.com/1589518
* Office Hours and GitHub Welcome Class
    * https://github.com/blog/970-more-github-office-hours-and-welcome-classes

# [#B] What is Git?
* Linux origins
* Why a distributed version control system?
* How does Git differ from previous VCS systems?

# [#A] Installing Git
* The 5 minute litmus test
* No systemic intrusions
* Ask for a USB Stick if you need binaries

# [#A] Creating Local Repositories
* `git init`
    * On exisiting code or folders
    * Legacy repo creation syntax
* `git init <REPONAME>`
    * For a brand new project
    * Recent convenience syntax (1.7 era)

# [#A] Configuring Git
* Git Config
    * Local
    * Global
    * System
* Your Name
    * git config --global user.name "Matthew McCullough"
* Your Editor
    * git config --global user.email "matthewm@ambientideas.com"
* Color
    * git config --global color.ui "auto"

# [#A] Adding and Commiting Basics
* Add
    * `git add <FILENAME>`
    * `git add <PATTERN>`
    * `git add *.html`
    * `git add src/`
    * `git add .`
    * Interactive selection of code
        * `git add -p`
* Commit
    * Making code a permanent part of history
    * Writing a commit to the .git/objects directory

# [#B] Three Stage Thinking
* Why Git has three trees
    * Working Directory (File System)
    * Staging Area (Index)
    * Repository (Commit History)
* Why Git has a staging area
    * Shopping cart
    * Select, then act
    * Durable between work sessions
* Why Git cares about content
    * Content tracker, not just a file tracker
    * Understands line (word) changes
    * Similarity index
    * Tracks code movement across renames, moves, and refactoring

# [#A] Git Hashing Basics
* Hashes
    * What is a hash?
    * Fingerprint
    * Unique content identification
* Hash Navigation Language
    * Commitish
    * Treeish

# [#B] DAGs & The Commit Graph
* Graph, with limitations
* Always traveling forward
* No loops
* New elements point to ancestors
* Liked linked lists

# [#A] Treeish, Commitish
* Graph navigation language
* Uses `^` and `~` and `@{}` and `...` symbols
* Use of subset of hash characters
    * 40 hex characters
    * 20 bytes
    * 160 bits
    * Can use as little as 4 characters
    * Standard is 7
* Two commits ago:
    * `HEAD@{2}`
* Two commits ago:
    * `HEAD^^`
* Two commits ago
    * `HEAD~2`
* Range from the local commits to the remote commits
    * `master..origin/master`

# [#A] More Precise Commit Contents
* Write code, change files
    * Separates changing files from commiting files
    * Can change more than you intend to commit
    * Can group what you changed for your commits
* Add only what's ready for consumption
    * Don't commit "less than ready" code
    * Stash away what you want to restore to pristine state
* Commit only a portion of file changes
    * Patch mode
        * git add -p
        * git stash -p
        * git reset -p
    * Stash
        * Put "away" entire files not ready for commit
        * Multiple stashes, but don't confuse them for real branches

# [#A] Cloning
* Hello Git World repo via three addresses
    * https://matthewmccullough@github.com/matthewmccullough/hellogitworld.git
    * git://github.com/matthewmccullough/hellogitworld.git
    * git@github.com:matthewmccullough/hellogitworld.git
* Each protocol type has minor differences
    * file://
    * git://
    * git+ssh://
    * http://
    * https://
    * Resulting repo is the same, no matter the protocol

# [#A] Branching Concepts
* Branches are cheap: 40 hex chars
    * Files in `.git/refs`
* Used to contain experiments, stories, and features.
* Branches begin life locally and are only published as requested
    * This makes branches suitable for experiments

# [#A] Basic Branching Mechanics
* TODO Creating branches for later
    * git branch <BRANCHNAME>
* Creating branches for immediate use
    * git checkout -b <BRANCHNAME>
* Deleting
    * `git branch -D <BRANCHNAME>`
    * `git branch -d <BRANCHNAME>`

# [#A] Reset
* Affects the index, possibly the current branch HEAD, and potentially working directory
* git reset --hard
    * Discard working directory and index
    * Defaults to HEAD
    * `git reset --hard HEAD`
    * `git reset --hard`
* git reset --soft
    * Destroy history, but leave working directory and stash the same
    * Permits a re-commit
    * `git reset --soft HEAD~1`
* git reset --mixed
    * `git reset --mixed`
# [#A] Remote Basics
* Just bookmarks for URLs
* One by default called `origin`
* Add as many as you like
    * Very different from centralized version control
    * `git remote add <REMOTENAME> <URL>`
    * Multiple named destinations for code

# [#B] Remote Details
* What gets retrieved from a remote?
    * Default refspec
    * Can address with greater precision with custom editing in .git/config
* Editing remotes
    * Adding
    * Removing
    * Renaming
* Why are remote branches immutable?
    * Local cache
    * Like browser cache

# [#B] Navigating the Tree
* diff
* ls-tree
* show

# [#B] Git Internals
* Plain Text Config
    * .gitconfig
    * .git/config
    * .git/HEAD
    * .git/FETCH_HEAD
    * .git/COMMIT_EDITMSG
* Git exposes its internals
    * Composed construction
    * Porcelain and plumbing
* Can discover the data structures
    * Git manipulates graphs
    * Many git commands just change file pointers in .git

# [#A] Network Operations
* Cloning
* Remotes
* Pushing
* Pulling
* Fetching

# [#A] Merging Basics
* Can merge tags, branches and arbitrary hashes
    * `git merge <TAG>`
    * `git merge <BRANCH>`
    * `git merge <9fa321e>`
* Outcomes
    * "merge made by recursive"
    * "fast-forward"
* `git merge <branch>`
* Which branches are merged?
    * git branch --merged
    * git branch --no-merged

# [#B] Merging Techniques
* Octopus
    * Multiple branches at once
    * More efficient than sequentially
* Strategies
    * `git merge -s ours <BRANCH>`
    * `-s subtree`
    * `-s ours`
    * There is no `theirs`
* No Commit (Pause)
    * `--no-commit`
    * Only works with recursive
    * Fast-forward will still commit (no merge commit)
* No Fast-Forward (Merge Commit Forced)
    * `--no-ff`
    * Force a merge commit, even if not needed
    * Provides permanent record of merge (and possibly the feature being merged in)
* Choosing a side per file
    * git checkout --ours <filename>
    * git checkout --theirs <filename>

# [#A] Rebasing
* Accomplishes
    * Code change clarity
    * Multi-commit unification
    * History linearity
    * Commit message cleanup
* Traditional rebase
    * Common to put the contents of one branch after the master branch
    * git rebase <COMMIT>
* Interactive rebase
    * User-involved rebasing to change order, message, contents
    * git rebase -i <COMMIT>
* Fixup
* Autosquash
* Leaving the merge bubble after rebase
    * Keeps visual representation of feature work
    * `merge --no-ff`

# [#B] Diff and Merge Tools (Visual)
* Difftool
    * `git difftool <REF1> <REF2>`
    * For staged and unstaged changes
    * Diffing arbitrary branches
    * Doesn't require any specific "state"
* Mergetool
    * `git mergetool`
    * For merge conflicts
    * Requires merge conflict to activate
* Configuration in .gitconfig
* Selection at CLI
    * `git difftool -t araxis`
    * `git mergetool -t araxis`
    * `git difftool -t opendiff`
* Default supported tools
    * `git help difftool`
    * P4Merge
    * OpenDiff
    * VimDiff
    * Araxis
    * BeyondCompare
    * Anything that accepts command line parameters

# [#A] History Modification
* Reset
* Amend
* Rebase
* Reflog

# [#B] Workflows
* Offline sharing
* Pushing and pulling
* Commander, lieutenant and soldier
* Centralized

# [#C] Dev Tool & IDE Git Integration
* Eclipse
* IntelliJ
* TextMate
* Emacs
* Vim
* Visual Studio

# [#C] Web Tools
* git instaweb
* viewvc
* bananajour

# [#C] Repo Hosting
* Web tools
* Gitolite
* Gitorious
* GitHub:Enterprise

* Git hosting

# [#B] Refspecs
* Control what is pulled
* Control what is pushed
* Notes
* Tags

# [#B] Precision Actions
* Merging a single file
    * git checkout 
* Displaying a file at a certain point in time
    * git show TREEISH:filename

# [#B] Broad Actions
* Logging ranges
    * git log SINCE..TO
* Diffing arbitrary hashes
    * git diff ANYFROM ANYTO

# [#B] Branching Strategies
* What code belongs where?
* Good branching
    * Small
    * Quickly merged
    * Well named
* Branch lifetimes
    * Long lived branches
    * Integration branches
    * Short lived (topic) branches
* Naming conventions
    * Slashes in the name?
    * Usernames in the branch name (like the git project)
    * ls-remote becomes more helpful
* Merge and rebase techniques from the field

# [#B] GitHub
* Hosted Git repos

# [#C] Hashing Examples In The Real World
* Names (3 letters + 1) on United screens
* First letter plus last on bulletins
* Trying to make a unique thing out of a non unique or large thing (full name)
* Trying to obscure the data but still offer a unique fingerprint

# [#B] Eclipse
* JGit
* EGit
* New 1.2 feautures such as patch mode staging
* Gists

# [#B] End of Class Q&A
* Tooling suggestions?
* Branch strategies?
* Git repo hosting?
* Git backup strategies?
* Getting code off developer laptops
* How to handle hooks
* Using GitHub
