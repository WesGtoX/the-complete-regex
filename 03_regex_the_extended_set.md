# Regular Expressions - POSIX

## The extended set

|Symbol      |What does it represents?|
|------------|------------------------|
|`+`         |One or more occurrences of the character that precedes this `+` symbol.|
|`?`         |Zero or more occurrences of the character that precedes this question mark.|
|`pat1\|pat2`|Matches either the pattern `pat1` or the pattern `pat2`.|
|`()`        |Divides patterns into groups.|
|`{m}`       |Exactly `m` occurrences of whatever precedes|
|`{m,n}`     |Atleast `m` and at most `n` occurrences of whatever precedes. Only one of `m`, `n` is mandatory. Other can be left blank.|

---

- `a{m}` - Represents exacly `m` repetitions of whatever immediately preces this, i.e. `a`.
```bash
grep -E '^[0-9]{3}$' regex18.txt
# 834
# 519
# 645
```

---

- `a{m,n}` - Represents at least `m` an most `n` repetitions of whatever immediately precedes this, i.e. `a`.
```bash
grep -E '^[a-z]{4,6}$' regex19.txt
# 123456 - number of character
# lion
# tiger
# mouse
# cuckoo
# deer
```

---

- Parenthesis is used to grou and treat as a single entity.
- `{m,}` - Represents at least `m` repetitions of whatever immediately precedes this.
```bash
grep -E '(ha){4,}' regex20.txt
# hahahahaha
# hahahaha
# hahahahahaha
# hahahahahahahaha
# hahahahahahahahaha
```

---

- Parenthesis is used to grou and treat as a single entity.
- `{,n}` - Represents at most `n` repetitions of whatever immediately precedes this.
```bash
grep -E '^(ha){,2}$' regex21.txt
# ha
# haha
```

---

- `a+` - One or more occurrences of `a` (The character just preceding the plus symbol).
```bash
grep -E 'fooa+bar' regex22.txt
# fooaaaabar
# fooabar
# fooaabar
```

---

- `a?` - Zero or one occurrences of `a` (The character just preceding the question mark).
```bash
grep -E 'https?://website' regex23.txt
# https://website
# http://website
```

---

- `(a|b)` - Represents either `a` or `b`, where `a` and `b` can be multi-character strings.
```bash
grep -E '(log|ply)wood' regex24.txt
# logwood
# plywood
```
