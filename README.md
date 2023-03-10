# QueryXSS

QueryXSS is a tool to test for reflected inputs in the response.

**Beware:** This tool is still in development, so you can expect bugs.

![](docs/img/example.png)

## Scanners

The list below shows the scanners that are currently implemented, and the ones that are planned to be implemented.

If you have any suggestions, feel free to open an issue.

| Name | Modifications | Implemented |
| --- | --- | --- |
| Simple | Requests the URL as it is, with no modifications. If it doesn't get any reflection and the query has special HTML characters, it will replace them and test again. | YES |
| ReplaceValuesHtmlChars | Replaces values in a query with HTML special characters. It detects if each special character reflects. | YES |
| PostfixValues | Appends a random token to every value in the query. | NO |
| ReplaceValues | Replaces values in a query with a random token. | NO |
| PostfixSpecialValues | Appends HTML special characters to every value in the query. | NO |

## Usage

```bash
$ queryxss -h                                    
QueryXSS finds reflected values in the HTTP response.

Usage:
  queryxss [flags]

Flags:
  -d, --debug                Enable debug mode
  -f, --file string          File with URLs to scan
  -H, --header stringArray   Headers to send with the request (specify multiple times)
                             Example: -H 'X-Forwarded-For: 127.0.0.1' -H 'X-Random: 1234'
  -h, --help                 help for queryxss
  -m, --min-length uint      Minimum value's length to scan for reflections (default 3)
  -n, --no-color             Disable color output
  -r, --rate-limit uint      Number of requests per second (default 25)
  -s, --silent               Outputs only errors and the results
```

## Install

### Using go install

Make sure you have [Go installed and configured](https://go.dev/doc/install).

```bash
go install github.com/vitorfhc/queryxss/cmd/queryxss@latest
```

### Manual install

```bash
git clone github.com/vitorfhc/queryxss
cd cmd/queryxss
go install
```