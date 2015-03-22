commit hooks

check files

diffable_files = `git diff --name-only --diff-filter=ACMRTUXB origin/master... | grep .md`.split("\n")

