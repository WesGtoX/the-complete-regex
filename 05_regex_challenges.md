# Challenges

## Challenge 01

- `([a-zA-Z0-9\_\.\-]{1,})` - Matches one or more string that has letters and numbers and only those characters `_`, `.`, `-`.
- `([a-zA-Z0-9]{1,}\.)` - Matches one or more strings that contain letters and numbers ending with a `.`.
- `([a-zA-Z0-9]{2,})$` - Matches a string that contracts 2 or more letters or numbers.
```bash
grep -E '^([a-zA-Z0-9\_\.\-]{1,})@([a-zA-Z0-9]{1,}\.){1,}([a-zA-Z0-9]{2,})$' challenge01.txt
# bob.123@gmail.com
# alice-personal@yahoo.in
# admin@cloud.guru
# tom_business@amazon.ca
```
