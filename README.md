# bash-documentation-and-best-practices

## Shebang
```shell
#!/usr/bin/env bash
...
```

## `if` ... `then` ... `else`
```shell
if [ condition ]; then
  ...
elif [ condition ]; then
  ...
else
  ...
fi
```

## Conditions
```shell
[ -f '/etc/hosts' ] && echo '/etc/hosts is a file'
[ -z '' ] && echo 'String is empty'
[ 'string-equality' == 'string-equality' ] && echo 'Strings are equals'
```
