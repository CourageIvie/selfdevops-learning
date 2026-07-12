
## Lesson: Heredoc Paste Corruption in YAML Files
- Never paste a `cat > file << 'EOF'` command into a file that's already open/being edited. That command belongs at the terminal prompt only. If it lands inside a file instead, YAML parsing breaks with errors like "could not find expected ':'" at the point where the stray command line appears.
- To diagnose a suspected corrupted file: use `cat -n filename` (numbered lines, read-only) or `sed -n 'START,ENDp' filename` to view specific line ranges without editing anything.
- To confirm a file's size/shape after a fix: `wc -l filename` (line count) and `cat -n filename | head -5` (confirm what the file actually starts with).
- To safely delete a known bad line range: always `cp filename filename.bak` first, then `sed -i 'START,ENDd' filename`.
- To fix one known bad value safely: `sed -i 's/OLD/NEW/' filename`, then verify with `grep KEYWORD filename` immediately after — never trust "done" as confirmation, always see the actual output.
- Rule of thumb: if a line of text has the shape `key: "value"` or looks like file content, it belongs in a file, not typed into the terminal prompt directly.

## Lesson: Detecting Accidental Service Loss in Compose Files
- Quick service inventory without opening the whole file: grep -n "^  [a-z-]*:" docker-compose.yml - lists every top-level service name and its line number. Fast way to spot duplicates or missing services.
- File size is a cheap sanity check: ls -la with multiple yml files - if your current file is dramatically smaller than your backups, something got lost. Compare before assuming a backup is stale.
- When multiple backups exist, compare all of them by service list before picking one to restore - dont assume the most recent bak is the most complete one.
- Always keep the broken version before overwriting, for example cp docker-compose.yml docker-compose.yml.broken-description - cheap insurance, costs nothing, saves you if the fix was wrong.
- If you accidentally paste multi-line file content directly into the terminal prompt instead of into a heredoc, bash will throw syntax errors on lines with parentheses or special characters. No file gets corrupted in this case, but always verify with cat filename afterward before assuming anything was written.

