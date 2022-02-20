# bash-documentation-and-best-practices

## Shebang
```shell
#!/usr/bin/env bash
...
```

## stdout / stderr
```shell
echo "Print to stdout"
>&2 echo "Print to stderr"
```

## `if` ... `then` ... `else`

```shell
if [[ condition ]]; then
  ...
elif [[ condition ]]; then
  ...
else
  ...
fi
```

## Conditions
```shell
# File conditions
[[ -f '/etc/hosts' ]] && echo '/etc/hosts is a file' || echo "or not"
[[ -d '/etc' ]] && echo '/etc/is a directory' || echo "or not"
```

```shell
# String conditions
[[ -z '' ]] && echo 'String is empty' || echo "or not"
[[ -n 'filled' ]] && echo 'String is non empty' || echo "or not"
[[ 'string-equality' == 'string-equality' ]] && echo 'Strings are equals' || echo "or not"
[[ 'string-contains-substring' =~ 'substring' ]] && echo 'String contains substring' || echo "or not"
[[ 'string-match regex' =~ ^.*-m.*\ r.*$ ]] && echo 'String match regex' || echo "or not"
```

```shell
Numbers
```

## Loops

### `while` ... `do` ... `done`

```shell
while [[ condition ]]; do
  ...
done
```

### `for` ... `do` ... `done`


## Function
```shell
function name() {
  local arg1; arg1=$1
  local arg2; arg2=$2

  [[ -z "${arg2}" ]] && { echo "Arg2 missing"; return 1; }

  local RESULT="${arg1}-${arg2}"
  echo ${arg1}
}

FUNCTION_RESULT=$(name "arg1" "arg2") || echo "An error occured"
echo "Function returns '${FUNCTION_RESULT}'"

FUNCTION_RESULT=$(name "arg1") || echo "An error occured: '${FUNCTION_RESULT}'"
```

## `.basrc` vs `.bash_profile`
