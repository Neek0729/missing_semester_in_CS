# Version control and Git

## Concepts
1. based on distributed graph theory tree model, could be considered as snapshot of data model.\
Git models a particular point in history as a collection of file and folders and encapsulates all these states as "snapshot"
2. In Git terminology, file is called **blob**, and folder is called as **tree**. 
3. Rather than stores a sequence of snapshots to control version, Git maintains the history by a **directed acyclic graph** of snapshots.\
[WIKI of 'directed acyclic graph'](https://en.wikipedia.org/wiki/Directed_acyclic_graph) \
This is to say, in Git, due the branching, each snapshot refers to a set of parents, not a single parent.\
4. Similar to time and history in real world, snapshots with relationship form an immutable data structure(can commit to merge but cannot modify the history directly)

## pseudocode for understanding Git
```
//PSEUDOCODE
type blob = array<byte>;                   // file
type tree = map<string, tree | blob>;      // directory or folder
                                           // map the name(str) to actual contents: tree name --> actual tree (w/ blob or subtree)
type commit = struct{
              snapshots     tree;
              parent        array<commit>; // recursive data structure: commits refer back to other commit
              author        string;
              change_msg    string;
};                                         // a bunch of different data structure
type object = blob | tree | commit         // object unified all above structure

objects = map<string, object>

```



