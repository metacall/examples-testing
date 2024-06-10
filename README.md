# Matacall Test Center
This is a test center for Matacall. It contains a set of test cases for Matacall projects and examples. The test cases are written in a specific yaml format, which is described in the following sections.
The main script used for testing is `metacall-test.py` and it is mainly used in the CI/CD pipeline of this repository. It can also used to test the projects locally.

## Test Suits Format
The test suits are written in a yaml format. The following is an example of a test suit for the [random-password-generator-example](https://github.com/metacall/random-password-generator-example)
```yaml
project: random-password-generator-example
repo-url: https://github.com/metacall/random-password-generator-example
code-files:
  - path: random-password-generator-example/app.py
    test-cases:
      - name: Check the password is generated in the correct length
        command: call getRandomPassword(12)
        expected-stdout: '\"[\w\W]{12}\"'
      - name: Check the password is generated in the correct length
        command: call getRandomPassword()
        expected-stdout: 'missing 1 required positional argument'
``` 

## Arguments
The following arguments are available for the `metacall-test.py` script:
```bash
> ./metacall-test.py -h
usage: metacall-test.py [-h] [-V] [-f FILE]

options:
  -h, --help            show this help message and exit
  -V, --verbose         increase output verbosity
  -f FILE, --file FILE  the test suite file name
```
Example:
```bash
./metacall-test.py -f  test-suits/test-time-app-web.yaml -V
```