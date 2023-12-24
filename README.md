## Introduction
`main.py` - This script can check for the latest open issues, find if they're applied or not, and apply to all opened issues or the last one only. These options are configurable using shell flags accepted by the script. The script only look for **Ordinary IPO shares**.

## Install

- Install `python3`
- Create an `accounts.csv` file with the same format as [accounts.csv.example](accounts.csv.example) 
- `python3 main.py --help` for help

    ```shell
    usage: main.py [-h] [-r] [-a] [-u USER] [-c COMPANY_SHARE_ID] [-n NUMBER_OF_SHARES]
    
    MeroShare simplified for bulk actions.
        - Find currently open issues
        - Check issue status (applied, unapplied, allotted or not-allotted)
        - Generate IPO allotment reports
    
    options:
      -h, --help            show this help message and exit
      -r, --report          Check IPO allotment reports
      -a, --apply           Apply to issues
      -u USER, --user USER  Run script for this user only, default is run for all users in accounts.csv file
      -c COMPANY_SHARE_ID, --company-share-id COMPANY_SHARE_ID
                            Company share ID to apply, required when -a/--apply flag is set
      -n NUMBER_OF_SHARES, --number-of-shares NUMBER_OF_SHARES
                            Number of shares to apply, default is 10
    ```

## Examples
### Apply IPO
1. List open IPOs:
    ```shell
    python3 main.py
    ```
   This will list the currently Open IPOs and status whether they're applied by the user or not. It'll also show the `COMPANY SHARE ID`, a unique ID associated with an IPO. You'll need this to apply the IPO.

2. Copy the `COMPANY SHARE ID` of the IPO you want to apply to.
3. Apply to IPO:
    ```shell
    python3 main.py -a -c 654 -n 10
    ```
    This will skip the user for which the IPO has already been applied.  
    If you'd like to apply IPO for a single user:
    ```shell
    python3 main.py -a -c 654 -n 10 -u ayerdines
    ```


## Usage
### Run script for a single user present in the `account.csv` file
```shell
python3 main.py -u <user>
```

### List open issues and check if they have been applied or not
```shell
python3 main.py
```

### Generate IPO allotment reports for a single user
```shell
python3 main.py -r -u <user>
```

### Generate IPO allotment reports for all users
```shell
python3 main.py -r
```
