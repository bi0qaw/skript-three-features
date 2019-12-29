# Patterns

Patterns are used to match code against definitions of expressions.
Historically, expressions were only intended to be defined from
java code and not in skript itself. This works well for very simple
code, but even code of moderate length requires the possibility to
define functions/expressions. Allowing the creation of expressions
in skript will make them much more common in code. So the syntax 
should be adapted.

The main point is that input parameters should map directly to 
variables used in code. For example:
```
expression teleport [entity] to [world]:
  # here [entity] and [world] are parameters
  # of the expression
  send "You are being teleported to [world]!" to [entity]
  ... # actual code to teleport entity
```

This is how parameter assignment works in pretty much every
programming langauge.


## Syntax for Expression Definition

- `literal` is just a bunch of text
- `[name=default: type]` is a nested pattern with name: `name`, default value: `default` and type: `type`
- `a|b` is either `a` or `b`
- `(pattern)` is a grouped pattern
- `<pattern>` is an optional pattern
- `{a: b}` is a custom pattern with name a and content b
