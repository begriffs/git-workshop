# History and Design Decisions

Git is the leader among modern version control. It feels pervasive, almost like a natural resource. It is not without history however. Learning the history of our tools helps us use them effectively and not repeat the mistakes that led to their creation. This article summarizes Linus Torvald's [presentation](http://www.youtube.com/watch?v=4XpnKHJAok8) at Google about prior version control systems and his design decisions for Git.

His three big decisions can be summarized as distribution, selective performance, and guaranteed data consistency. Git's distributed design reflects the ways developers actually collaborate and trust one another. It is efficient in precisely the ways which promote developers' good habits. Finally, it scrupulously guards data against corruption and malice.

## The choice to be distributed

Linus' first choice was to make Git fundamentally distributed. There is no central server, in fact no repository clone is more important than any other. Technical concerns aside, this reduces political friction during project maintenance. No central authority is required to establish or limit commit access to a group of designated contributors. Anyone can clone a project, and change it. These changes may or may not be attractive to the original project maintainers who can choose to incorporate them.

Although Git allows anyone to clone code and tinker, it doesn't remove the need for trust. It actually embraces the way people trust each other. Project maintainers trust certain contributors, who in turn trust others. Accepting code changes from people we trust requires less diligence, and is more pleasant. This distributed network of trust is how people naturally work, how we're wired. Git's distributed architecture mirrors our natural behavior. Older version control systems such as SVN force trust to happen at a single point, which hinders delegation among programmers.

A distributed design also relieves maintainers the duty of merging every difficult source change. As their project grows and matures they don't always have detailed knowledge of every subsystem. If a subsystem expert submits a patch that doesn't merge cleanly then the maintainer can ask them to do the merge themselves &mdash; by updating their own repository, merging there, and resubmitting the revision.

Repository copies are autonomous. This has implications beyond the trust and delegation already mentioned. Developers can do &mdash; and track within Git &mdash; whatever they want in their local copies without any of their experiments being at all visible to the project as a whole. This provides a healthy place to experiment. It wasn't always this way. Centralized VCMs of yore exposed experiments and works-in-progress (called branches) to everyone on a project. Developers had to deal with irrelevant details such as temporary branch namespacing.

## The choice to be fast &mdash; especially where it counts

True performance is not about doing the same old thing faster, it's about shaping and improving behavior. Look primarily at what matters and optimize that. Older VCSs brag that their branch creation operation is fast, but neglect to say that the inevitable merge operation is slow and difficult. This is disingenuous. Linus chose to optimize the merge operation in Git. It allows developers' changes to harmonize and will be covered later in this workbook. Convenient branching and merging means people do it more, which shapes their development behavior. This is true optimization.

Git does not internally track changes on a per-file basis. It is relatively slow to display the history of a single file. However it is fast at showing the history of collections of files and of the entire repository. Top level maintainers of a big project are more interested in seeing project changes in broad strokes. Bug reports are often vague, and a maintainer wants to see generally how subsystems have changed in ways that might pertain to the bug. Linus believes that this bulk comparison operation is necessary for a useful SCM.

Because Git is distributed, when you clone a repo you will receive its entire history. This makes cloning large repositories slow. To compensate, Git allows repositories to embed others via pointers. Linus believes that this is a blessing in disguise, because it encourages developers to separate large projects into logical submodules.

## The choice to stringently protect data

Git was designed to be reliable. It creates a unique signature called a "hash" for every change to a repository. This hash represents not only the current state of the data, but all the changes it has undergone. Some people inferred that the cryptographic-grade hashing algorithm that Git uses, SHA-1, is for security purposes. This is not the case, in reality Linus chose it because he was serious about avoiding collisions, that is identical signatures created for different repository histories.

If you know the SHA hash for your repository then you can trust the history all the way back. Git is an SCM that supports the longevity of your projects. Errors introduced by disk corruption, change of storage medium, or data transmission will be caught. While operating on your data you can be sure that restoring it to a known SHA-1 hash will be exactly back to the state you trust.

Ultimately Git assures you get out what you put in. You shouldn't have to discover disk corruption by randomly noticing a change in your code. The Git internals are very simple and are built around trust and reliability.
