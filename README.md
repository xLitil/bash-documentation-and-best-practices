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
  continue # exit from current iteration and begin the next iteration.
  break # exit from the while 
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

## Template

```shell
#!/usr/bin/env bash

CURRENT_SCRIPT_PATH=$( cd "$(dirname "${BASH_SOURCE[0]}")" ; pwd -P )

CMD_NAME="$0"

usage() {
  echo "Usage: $CMD_NAME {start|stop|restart|status}"
  echo
  echo "Options:"
  echo "  start: start application, see $CMD_NAME start -h for further information."
  echo "  stop: gently stop or not if timeout reached."
  echo "  restart: stop then start"
  echo "  status: indicate if application process is running or not."
}

start() {
  while true; do
    case "$1" in
    -p | --http-port)
      APP_HTTP_PORT=$2
      shift 2
      ;;
    -s | --https-port)
      APP_HTTPS_PORT=$2
      shift 2
      ;;
    --)
      shift
      break
      ;;
    *) break ;;
    esac
  done
  
  echo "..."
}

case "$1" in
start)
  shift
  start $@
  ;;
stop)
  shift
  stop
  ;;
restart)
  shift
  stop
  start
  ;;
status)
  status
  ;;
-h | --help | *)
  usage
  exit 1
  ;;
esac
```
