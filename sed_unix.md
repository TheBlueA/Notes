### replace str by regex in test (first match )
```
sed "s/regex/replaceString/" test.txt
```

### replace str by regex in test (all matches ) , the result will save in match.txt
sed "s/regex/replaceString/g" test.txt > match.txt
