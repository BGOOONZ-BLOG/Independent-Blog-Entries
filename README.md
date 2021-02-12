# Based on the a/A Open cirriculumn

for f in *.html; do printf '%s\n' 0a '<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>;' . x | ex "$f"; done


case $BASH_VERSION in ''|[123].*) echo "ERROR: Bash 4.0+ required" >&2; exit 1;; esac
shopt -s globstar
for d in ./**/**/**/ ; do (for f in **.html; do printf '%s\n' 0a '<!DOCTYPE html><html lang="en"><head>  <meta charset="UTF-8">  <meta name="viewport" content="width=device-width, initial-scale=1.0">  <title>Document</title></head><body>;' . x | ex "$f"; done); done


find . -name '*.html' -type f -exec echo -e '<!DOCTYPE html><html lang="en"><head>  <meta charset="UTF-8">  <meta name="viewport" content="width=device-width, initial-scale=1.0"> <title>Document</title></head><body>'| tee -a *.html '{}' +



find . -name '*.html' -exec sh -c '(echo HEAD;cat {};echo FOOT) > {}.tmp && mv {}.tmp {}' \; -print



gawk -i inplace 'BEGINFILE{print "<!DOCTYPE html><html lang="en"><head>  <meta charset="UTF-8">  <meta name="viewport" content="width=device-width, initial-scale=1.0"> <title>Document</title></head><body>"};ENDFILE{print "APPEND"};1' ./*.html


find . -type d -exec bash -c 'for f; do mv "$f" "${f// /_}"; done' _ {} +



find . -type d -exec bash -c 'for f; do mv "$f" "${f// /_}"; done' _ {} +



find . -type f | for f in *.html; do printf '%s\n' 0a '<!DOCTYPE html><html lang="en"><head>  <meta charset="UTF-8">  <meta name="viewport" content="width=device-width, initial-scale=1.0">  <title>Document</title></head><body>;' . x | ex "$f"; done


find . -type d -exec bash -c 'for f in *.html; do printf '%s\n' 0a '<!DOCTYPE html><html lang="en"><head>  <meta charset="UTF-8">  <meta name="viewport" content="width=device-width, initial-scale=1.0">  <title>Document</title></head><body>;' . x | ex "$f"; done' _ {} +



awk '$0="<!DOCTYPE html><html lang="en"><head>  <meta charset="UTF-8">  <meta name="viewport" content="width=device-width, initial-scale=1.0">  <title>Document</title></head><body>"$0' file > new_file





FOLDER='.'
TEXT='<!DOCTYPE html><html lang="en"><head>  <meta charset="UTF-8">  <meta name="viewport" content="width=device-width, initial-scale=1.0"> <title>Document</title></head><body>'
cd $FOLDER
for i in `ls -1 $FOLDER`; do
     CONTENTS=`cat $i`
     echo $TEXT > $i  # use echo -n if you want the append to be on the same line
     echo $CONTENTS >> $i
done






#!/usr/bin/env bash

# define the function we're going to export for access from a subprocess
do_prepend() {
  local name new_name old_quotes='"' new_quotes="'"
  for f in *.html; do printf '%s\n' 0a '<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>;' . x | ex "$f"; done
}
export -f do_replace # actually export that function

# tell find to start a new copy of bash that can run the function we exported
# in each directory that contains one or more file or directory names with quotes.
# Using ``-execdir ... {} ';'`` to work around a MacOS bug
# ...use ``-execdir ... {} +`` instead with GNU find for better performance.
find . -depth -name '*"*' -execdir bash -c 'do_prepend "$@"' _ {} ';'










  for f in *./**/**/**/**/*.html; do printf '%s\n' 0a '<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>;' . x | ex "$f"; done



#!/usr/bin/env bash

# define the function we're going to export for access from a subprocess
do_replace() {
  local name new_name old_quotes='"' new_quotes="'"
  for name do  # loops by default over "$@", the argument list given to the function
    new_name=${name//$old_quotes/$new_quotes}
    mv -- "$name" "$new_name"
  done
}
export -f do_replace # actually export that function

# tell find to start a new copy of bash that can run the function we exported
# in each directory that contains one or more file or directory names with quotes.
# Using ``-execdir ... {} ';'`` to work around a MacOS bug
# ...use ``-execdir ... {} +`` instead with GNU find for better performance.
find . -depth -name '*"*' -execdir bash -c 'do_replace "$@"' _ {} ';'






#!/usr/bin/env bash
# WARNING: This calculates the whole glob before it runs any renames; this can be very
# inefficient in a large directory tree.

case $BASH_VERSION in ''|[123].*) echo "ERROR: Bash 4.0+ required" >&2; exit 1;; esac
shopt -s globstar
for f in **; do
  echo -n '<!DOCTYPE html><html lang="en"><head>  <meta charset="UTF-8">  <meta name="viewport" content="width=device-width, initial-scale=1.0"> <title>Document</title></head><body>'; cat file; } >file.new
 mv file{.new,}
done
