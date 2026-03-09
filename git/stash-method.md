The "Stash" Method (Recommended)

If you aren't ready to commit the backend work yet but want to move it out of the way safely, use the Stash. This puts your current changes into a temporary storage area.

Stash your changes:
```bash
git add . (to track the new folder)
git stash
```

Switch branches:
```bash
git checkout your-branch-name
```

Bring the changes back (Optional):
If you actually wanted those changes on your other branch, run:
```bash
git stash pop
```