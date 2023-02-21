# Notes about rlib

## Possible Todos

- Ci pipeline is failing right now on every commit.
  Error
  ```text
  fatal: unable to access 'https://gitlab.redox-os.org/redox-os/core_io.git/': server certificate verification failed. CAfile: none CRLfile: none
  ```
- The project is still in the phase of implementing the API. There are a lot of functions waiting to
  implemented. Can be find with following command
  ```sh
  grep -nr "unimplemented!()"
  ```
  There are also some TODOS
  ```sh
  grep -nr "TODO"
  ```
- Some things mentioned the MakeFile under tests
    - dynamic tests currently broken
    - Some functions must be fixed 
	    - mkfifo
	    - netdb/netdb 
