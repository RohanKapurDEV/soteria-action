# GitHub Action for Soteria
This action enables you to run the Solana smart contract vulnerability scanning tool Soteria as part of your CI/CD pipeline in the simplest possible way. There are several ways you can optimise the job and tweak it, but this action aims to make things easy!

## Action inputs :ballot_box:
The action takes the following inputs, but note that they are not required. 
If this is new to you, just run the action without passing any arguments!
```
solana-version (default: "1.9.5")        - Check Solana releases if needed
run-mode       (default: "-analyseAll")  - Runs the tool against all contracts
cargo-com      (default: ".")            - Shortcut Cargo build command
program-path   (default: ".")            - Add path to a specific program / path
```

## Running the Action in GitHub CI :infinity:
You can use this Action as part of your project by creating an Action as follows:
```
name: Soteria Scan
# Update this to match your branch names and requirements
on:
  push:
    branches: main
  pull_request:
    branches: main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check-out the repository
        uses: actions/checkout@v2
      - name: Soteria Scan
        continue-on-error: false  # set to true if you don't want to fail jobs
        uses: silas-x/soteria-action@v0.3
        with:                     # remove if not passing arguments below
          solana-version: "1.9.5" # not required
          run-mode: "-analyzeAll" # not required
          cargo-com: "."          # not required
          program-path: "."       # not required
 ```
 
 ## Managing false positives :space_invader:
 The tool may identify potential issues that you accept as they are to e.g. save compute cycles, or genuine false positives.
 Ignores can be configured by adding the below annotation to the line above the line you are wanting to ignore:
 ```
//#[soteria(ignore)]
 ```
 
 ## Feedback :fist_right::fist_left:
 Please raise an issue for suggestions and any bugs related to the Action.
 
 If you feel this Action has helped your project, donations are welcome to this SOL address: _Db4eiNsEXQ5gUZsxGWchj39CXQZ1ZGuuaS4MdSobVhtT_
 
 Made with :heart: by silas

 ## Responsibility :call_me_hand:
 I am not the author of Soteria. I can't answer support questions related to the tool and I take no responsibility of the accuracy of it, 
 or the outcomes of running this Action. You should not solely rely on the the results of running this tool, as no tool will be able to
 provide assurance of security or completeness of a smart contract. Use at own risk and see licence note for further information.

