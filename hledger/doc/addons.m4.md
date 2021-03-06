# ADD-ON COMMANDS

hledger also searches for external add-on commands, and will include these in the commands list.
These are programs or scripts in your PATH whose name starts with `hledger-`
and ends with a recognised file extension 
(currently: no extension, `bat`,`com`,`exe`, `hs`,`lhs`,`pl`,`py`,`rb`,`rkt`,`sh`).

Add-ons can be invoked like any hledger command, but there are a few things to be aware of.
Eg if the `hledger-web` add-on is installed,

- `hledger -h web` shows hledger's help, while `hledger web -h` shows hledger-web's help.
  
- Flags specific to the add-on must have a preceding `--` to hide them from hledger.
  So `hledger web --serve --port 9000` will be rejected; you must use `hledger web -- --serve --port 9000`.

- You can always run add-ons directly if preferred: `hledger-web --serve --port 9000`.

Add-ons are a relatively easy way to add local features or experiment with new ideas.
They can be written in any language, but haskell scripts have a big advantage:
they can use the same hledger (and haskell) library functions that built-in commands do,
for command-line options, journal parsing, reporting, etc.

Here are some hledger add-ons available:

## Official add-ons

These are maintained and released along with hledger.   

### api
[hledger-api](hledger-api.html) serves hledger data as a JSON web API. 

### ui
[hledger-ui](hledger-ui.html) provides an efficient curses-style interface. 

### web
[hledger-web](hledger-web.html) provides a simple web interface.

## Third party add-ons

These are maintained separately, and usually updated shortly after a hledger release.

### diff

[hledger-diff](http://hackage.haskell.org/package/hledger-diff)
shows differences in an account's transactions between one journal file and another.

### iadd

[hledger-iadd](http://hackage.haskell.org/package/hledger-iadd)
is a curses-style, more interactive replacement for the [add command](/hledger.html#add). 

### interest

[hledger-interest](http://hackage.haskell.org/package/hledger-interest)
generates interest transactions for an account according to various schemes. 

### irr
[hledger-irr](http://hackage.haskell.org/package/hledger-irr)
calculates the internal rate of return of an investment account.

## Experimental add-ons
  
These are available in source form in the hledger repo's bin/ directory; 
installing them is [pretty easy](/download.html#d).
They may be less mature and documented than built-in commands.
Reading and tweaking these is a good way to start making your own!

### autosync

[hledger-autosync](https://github.com/simonmichael/hledger/blob/master/bin/hledger-autosync) 
is a symbolic link for easily running 
[ledger-autosync](https://pypi.python.org/pypi/ledger-autosync), if installed. 
ledger-autosync does deduplicating conversion of OFX data and some CSV formats,
and can also download the data 
[if your bank offers OFX Direct Connect](http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings). 

### budget

[hledger-budget.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-budget.hs#L10)
adds more budget-tracking features to hledger.

### chart

[hledger-chart.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-chart.hs#L47)
is an old pie chart generator, in need of some love.

### check

[hledger-check.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-check.hs)
checks more powerful account balance assertions.

### check-dates

[hledger-check-dates.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-check-dates.hs#L15)
checks that journal entries are ordered by date.

### check-dupes

[hledger-check-dupes.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-check-dupes.hs#L21)
checks for account names sharing the same leaf name.

### equity

[hledger-equity.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-equity.hs#L17)
prints balance-resetting transactions, useful for bringing account balances across file boundaries. 

### prices

[hledger-prices.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-prices.hs)
prints all prices from the journal.

### print-unique

[hledger-print-unique.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-print-unique.hs#L15)
prints transactions which do not reuse an already-seen description.

### register-match

[hledger-register-match.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-register-match.hs#L23)
helps ledger-autosync detect already-seen transactions when importing.

### rewrite

[hledger-rewrite.hs](https://github.com/simonmichael/hledger/blob/master/bin/hledger-rewrite.hs#L28)
Adds one or more custom postings to matched transactions.

