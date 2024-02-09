# Optional Assigment and Optional Operators

## Introduction

Based on tangents in this discussion: https://es.discourse.group/t/optional-chaining-assignment/1149/14
This proposal does not implicitly check the whole path on the left-hand side. The justification for not doing that is it would hide a lot of branching.

Optional chaining removed a lot of verbose ```if``` statements; however, it did not apply to left hand side checks which are very similar.

```js
	a?.b?.c?.d();
```

When a similar property access is done on the left hand side an ```if``` is required.

```js
if (a?.b?.c?.d) {
	a.b.c.d = 1;
}
```

This proposal would add a new prefix to all assignment operators like: ```?<assignment operator>```.

```js
a?.b?.c?.d ?= 1;
```

If most of the path exists then optional assignment 

```js
const a = { b: { c: {} } };
a.b.c.d ?+= 1;
a; // { b: { c: {} } }
```

