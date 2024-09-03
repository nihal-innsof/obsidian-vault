---
id: Usefull commands (linux)
aliases: []
tags:
  - awk
---

- ## Convert multiline text to line single line

  Can be used to convert crypto keys so as to put them in _.env_ and _cli's_

  ```bash
  awk 'NF {sub(/\r/, ""); printf "%s\\n",$0;}' <filename>
  ```

  This **awk** command subfunction removes each line break (`\r`), and prints output without new line, adding **`\n`** text after each line read, ultimately generating a single line output. This can optionally be redirected to a file as desired.
