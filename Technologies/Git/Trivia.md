
# Origin
- Was created by the creator of linux `Linus Torvalds` in 2005 because he got screwed over by an older version control company called BitKeeper, he created linux as a free open source operating system, and BitKeeper put access to the BitKeeper services behind a pay wall, so now people needed to pay BitKeeper to access the free open-source linux, so Linus and the open-source community came together and created Git

---

# Architecture
- Git Object
	- Blob: binary large object --> contents and meta data of files
	- Tree: --> Folders and Directories
	- Commit:  the wrapper object that shows the meta data about the commit, and points to the tree object inside it
	- Tagged annotation

![[Git 3-tree Architecture.png]]