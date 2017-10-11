# Run Periodically

A simple tool to run tasks/jobs periodically.

## How to install

There is a [single shell script in src the directory](src/run-periodically). Just copy it into `/usr/local/bin` and give it permission to execute: `chmod a+x /usr/local/bin/run-periodically`.

## Usage

```
$ run-periodacally [OPTIONS] command comand-args...
```

### Options

* `--interval=seconds ` 
How many seconds to repeat command (starts counting at the end of the previous execution). Default: 10
* `--timeout=seconds` 
Timeout limit for command execution. If reach timeout, a SIGTERM will send to command asking him to exit. Default: 0 (inifinity timeout)
* `--kill-after=seconds` 
When a timeout is reached, if the command not exits with SIGTERM, it will be killed after the kill-after seconds. Default: 30
* `--max-consecutive-errors=integer` 
The maximum number of consecutive errors that will be tolerated. When this limit is reached, run-periodacally will terminate and the command will no longer being repeated until run-periodacally is started again. Default: 0
* `--interval-between-errors=seconds` 
Use a custom interval between errors instead of interval. Default: 0 (If 0, `--interval` value is used).

### Example

```
$ run-periodacally --interval=300 --timeout=120 --kill-after=10 --max-consecutive-errors=5 --interval-between-errors=1800 ./my-task.sh arg1 arg2 arg3
```

## Contribute

Pull requests are welcome!
