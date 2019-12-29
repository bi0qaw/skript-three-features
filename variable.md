# Variables

## Basic Properties

1. `[square]` brackets are used to denote variables
2. `[local]` variables have no prefix
3. `[-global]` variables are prefixed with a hyphen and stored in memory
4. `[_database]` variables are prefixed with an underscore and saved to the database
5. `[@option]` variables are prefixed with an at sign and replaced by their content at parse time
6. everything is a list variable
7. list entries are separated by simple dots
8. `[nested.[variables]]` are automatically evaluated
9. `"[variables]"` in strings are automatically evaluated
10. variables should behave like ordered dictionaries
11. `[(expressions)]` in variables have to be surrounded by parentheses

The choice of `[]` to denote variables is two-fold. Firstly, variables are all about 
putting stuff in a box and giving it a name. Brackets look at lot more like boxes than
curly parens. Furthermore it is an aesthetical choice. Brackets create a lot less noise
in the code than braces. Just look at the following piece of code. The one with
curly parens is much harder to read:

```
set [list.[index]] to [some.[nested].[value]]
set {list.{index}} to {some.{nested}.{value}}
```

---

## Using Simple and Nested Selectors

Variables can become deeply nested and accessing them very verbose.
Especially copying the index of one variable to another one should
be possible without a hassle. For this we can introduce simple (`*`) and
nested (`**`) selectors. Some examples:


```
set [a.parent] to "parent value"
set [a.parent.child] to "child value"

# indices are copied by default
# * is used to copy a single level of a list
set [b.*] to [a.*]
[b.parent] = "parent value"

# ** is used to copy all levels of a list
set [b.*] to [a.**]
[b.parent] = "parent value"
[b.parent.child] = "child value"

# only copying the values is also possible
set [b.*] to values of [a.*]
[b.1] = "parent value"

# same for indices
set [b.*] to indices of [a.*]
[b.1] = "parent value"

# selectors at lower levels should also be possible
set [b.*] to [a.*.child]
[b.parent] = "child value"

# selectors should also work for setting variables
set [b.*.child] to [a.*.child]
[b.parent.child] = "child value"
```
