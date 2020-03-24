# RegEx - Find and Replace with Capture Groups

- `sed` - Can search for a pattern and replaced with a substitution string all in a single line.
- `([0-9]+)` - Group 1.
- `([0-9]+)` - Group 1.
- `\1 pix by \2 pix` - Replacement string.
```bash
# Example
sed -r 's/pattern/replacement/g' inputfile

sed -r 's/([0-9]+)x([0-9]+)/\1 pix by \2 pix/g' regex25.txt
# 1280 pix by 720 pix
# 1920 pix by 1080 pix
# 1600 pix by 900 pix
# 1280 pix by 1024 pix
# 800 pix by 600 pix
# 1024 pix by 768 pix
```

---

- `([a-zA-Z]+)` - Group 1.
- `([a-zA-Z]+)` - Group 2.
- `\2,\1` - Replacement string.
```bash
sed -r 's/([a-zA-Z]+)\s([a-zA-Z]+)/\2,\1/g' regex26.txt
# Wallace,John
# King,Steve
# Cook,Martin
# Smith,Adam
# Peter,Irene
# Johnson,Alice
```

---

- `([0-9]{1,2})` - Group 1.
- `([0-9]{2})` - Group 2.
- `\2 mins past \1` - Replacement string.
```bash
sed -r 's/([0-9]{1,2}):([0-9]{2})/\2 mins past \1/g' regex27.txt
# 32 mins past 7
# 12 mins past 6
# 23 mins past 12
# 23 mins past 1
# 33 mins past 11
# 21 mins past 4
```

---

- `([0-9]{4})` - Group 1.
- `xxx.xxx.\1` - Replacement string.
```bash
sed -r 's/[0-9]{3}\.[0-9]{3}\.([0-9]{4})/xxx.xxx.\1/g' regex28.txt
# xxx.xxx.3013
# xxx.xxx.2589
# xxx.xxx.3147
# xxx.xxx.3698
# xxx.xxx.2145
# xxx.xxx.3369
```

---

- `([a-zA-Z]{3})` - Group 1.
- `([0-9]{1,2})` - Group 2.
- `([0-9]{2})` - Group 3.
- `\2-\1-\3` - Replacement string.
```bash
sed -r 's/([a-zA-Z]{3})\s([0-9]{1,2})[a-z]{2}\s[0-9]{2}([0-9]{2})/\2-\1-\3/g' regex29.txt
# 5-Jan-87
# 26-Dec-10
# 2-Mar-23
# 1-Oct-08
# 3-Aug-09
# 10-Jun-01
```

---

- `([0-9]{3})` - Group 1.
- `(\.[0-9]{3}\.[0-9]{4})` - Group 2.
- `\1\2` - Replacement string.
```bash
sed -r 's/\(([0-9]{3})\)(\.[0-9]{3}\.[0-9]{4})/\1\2/g' regex30.txt
# 914.582.3013
# 873.334.2589
# 521.589.3147
# 625.235.3698
# 895.568.2145
# 745.256.3369
```