# Regular Expressions - POSIX

## The basic set

|Symbol|What does it represents?|
|------|------------------------|
|`*`       |Zero or moreoccurrencies of the character that precedes this asterisk.|
|`.`       |A wildcar that represents any character.|
|`\s`      |Represents whitespace.|
|`[pqr]`   |A single character which can be either a `p`, `q` or an `r`.|
|`a-d`     |A single character that falls in the range `a-d`, i.e. one of `a`.|
|`^pq`     |A single character that is neither `p` nor `q`.|
|`^pattern`|`^` is an anchor tag that represents the beginning of the line.|
|`pattern$`|`$` is an anchor tag that represents the end of the line.|

---

- `.` - Single wildcard. Can represent any ONE character in a single position.
```bash
grep 'foo.bar' regex02.txt
# fooabar
# fooxbar
# foocbar
```

---

- `.*` - Zero or more occurrences of wilcard, which means zero or more occurrencies of any character.
```bash
grep 'foo.*bar' regex03.txt
# foobar
# fooabcbar
# foobxcbar
# foozbar
```

---

- `\s` - Represents whitespace. `\s*` represents zero or more occurrences of whitespace.
```bash
grep 'foo\s*bar' regex04.txt
# foo   bar
# foo bar
# foo      bar
# foobar
```

---

- `[abc]` - Character class. One of the characters inside the square brackets - `a`, `b` or `c`.
```bash
grep '[fcl]oo' regex05.txt
# foo
# coo
# loo
```

---

- `[abc]` - Character class. One of the characters inside the square brackets - `a`, `b` or `c`.
```bash
grep '[fcdplb]oo' regex06.txt
# foo
# coo
# doo
# poo
# loo
# boo
```

---

- `[^abc]` - Any character EXCEPT any of the ones inside the square brackets, in a single position.
```bash
grep '[^mh]oo' regex07.txt
# foo
# coo
# doo
# poo
# loo
# boo
```

---

- `[a-c]` - One of the characters falling in the range given in square brackets - `a`, `b`, `c`.
```bash
grep '[j-m]oo' regex08.txt
# joo
# koo
# loo
# moo
```

---

- `[a-cx]` - One of the characters falling in the range OR any of the other choices given in square brackets - `a`, `b`, `c`, `x`.
```bash
grep '[j-mz]oo' regex09.txt
# joo
# koo
# loo
# moo
# zoo
```

---

- `[a-cA-Cx]` - One of the characters falling in one of the ranges OR any of the other choices given in square brackets - `a`, `b`, `c`, `A`, `B`, `C`, `x`.
```bash
grep '[j-mJ-Mz]oo' regex10.txt
# joo
# Koo
# Loo
# moo
# zoo
```

---

- Following charactes shoul be escaped with a backlash as these characters have special meaning otherwise: `^$*.[()\`
```bash
grep 'x*\.y*' regex11.txt
# xxx.yy
# xx.yyyy
# x.yy
```

---

- If a `.` is insie square brackets, it nee NOT be escaped.
```bash
grep 'x[#:.]y' regex12.txt
# x#y
# x:y
# x.y
```

---

- If any of the characters `^,-` appear inside square brackets, it needs to be escaped with a backslash as these two charactes have special meaning inside square brackets.
```bash
grep 'x[#:\^]y' regex13.txt
# x#y
# x:y
# x^y
```

---

- The backslash itself should always be escaped with a backslash, irrespective of its position within the regex: `\\`
```bash
grep 'x[#\\\^]y' regex14.txt
# x#y
# x\y
# x^y
```

---

- `^` - Is a placeholder that signifier beginning of a line. The interpretation of `^` differs within square brackets and outside of it. Inside square brackets, '^' stands for negation. Outside, it is a placeholder for beginning of line.
```bash
grep '^foo.*' regex15.txt
# foo bar baz
# foo baz bar
```

---

- `$` is a placeholder that signifies end of la line.
```bash
grep '.*bar$' regex16.txt
# baz foo bar
# foo baz bar
```

---

- `^` is a placeholder that signifies beginning of a line; `$` is a placeholder tha signifies end of a line.
```bash
grep '^foo$' regex17.txt
# foo
```
