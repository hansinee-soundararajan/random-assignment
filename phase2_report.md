1.git revert 

C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git revert HEAD\~1

\[master 0645b75] Revert "extra"

&#x20;1 file changed, 1 insertion(+), 2 deletions(-)



after reverting the extra commit was undone



revert does not erase the history the changes are done by keeping the history intact.



2\. reflog shows the switching between branches the head pointer's movement.

C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git reflog

e53259a (HEAD -> master) HEAD@{0}: checkout: moving from branch-three to master

de30640 (branch-three) HEAD@{1}: reset: moving to HEAD

de30640 (branch-three) HEAD@{2}: checkout: moving from branch-three to branch-three

de30640 (branch-three) HEAD@{3}: checkout: moving from master to branch-three

e53259a (HEAD -> master) HEAD@{4}: commit: phase2\_report.md added

0645b75 HEAD@{5}: revert: Revert "extra"

9767e3e HEAD@{6}: commit: new file added

223641f HEAD@{7}: commit: extra

de30640 (branch-three) HEAD@{8}: checkout: moving from branch-three to master

de30640 (branch-three) HEAD@{9}: checkout: moving from master to branch-three

de30640 (branch-three) HEAD@{10}: commit (cherry-pick): Recreated commit



git log shows the commits done the history about each commit but reflog shows the movement



reflog has the history all the head movements that will be recorded



3\. Interactive rebase: 

It can be used to squash multiple commits into one, reorder commits, edit commit messages, or remove unnecessary commits.



Squashing commits is useful before merging because one commit does all the job toegther 



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git add README.md



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git commit -m "rebase commit4"

\[rebase-demo ad90737] rebase commit4

&#x20;1 file changed, 1 insertion(+), 1 deletion(-)



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git rebase -i HEAD\~3

\[detached HEAD d40d0fb] Implement rebase demo changes# This is a combination of 3 commits.

&#x20;Date: Tue Jun 23 12:03:14 2026 +0530

&#x20;1 file changed, 4 insertions(+)

Successfully rebased and updated refs/heads/rebase-demo.



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git log --oneline

d40d0fb (HEAD -> rebase-demo) Implement rebase demo changes# This is a combination of 3 commits.

07b87c0 rebase commit1

a090c65 (recovery, branch-one) branch-one changes

8546f34 commit 1



4.CHERRY PICK

C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git switch feature-a

Switched to branch 'feature-a'



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git add .



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git commit -m "new change"

On branch feature-a

nothing to commit, working tree clean



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git log --oneline

8fd5465 (HEAD -> feature-a, feature-b) phase2 modified

e4a4fcc phase2 modified

d40d0fb (rebase-demo) Implement rebase demo changes# This is a combination of 3 commits.

07b87c0 rebase commit1

a090c65 (recovery, branch-one) branch-one changes

8546f34 commit 1



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git add .



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git commit -m "new change"

\[feature-a 7b74d39] new change

&#x20;1 file changed, 1 insertion(+), 3 deletions(-)



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git log --oneline

7b74d39 (HEAD -> feature-a) new change

8fd5465 (feature-b) phase2 modified

e4a4fcc phase2 modified

d40d0fb (rebase-demo) Implement rebase demo changes# This is a combination of 3 commits.

07b87c0 rebase commit1

a090c65 (recovery, branch-one) branch-one changes

8546f34 commit 1



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git switch feature-b

Switched to branch 'feature-b'



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git cherry-pick 7b74d39

\[feature-b bee24c5] new change

&#x20;Date: Tue Jun 23 12:35:59 2026 +0530

&#x20;1 file changed, 1 insertion(+), 3 deletions(-)



C:\\Users\\hansi\\OneDrive\\Desktop\\desktop\\sample>git log --oneline

bee24c5 (HEAD -> feature-b) new change

8fd5465 phase2 modified

e4a4fcc phase2 modified

d40d0fb (rebase-demo) Implement rebase demo changes# This is a combination of 3 commits.

07b87c0 rebase commit1

a090c65 (recovery, branch-one) branch-one changes

8546f34 commit 1





"git cherry-pick 7b74d39" was cherry picked.



helps copy a specific commit from another branch to your current branch, creates a new commit on your branch with the same changes.







