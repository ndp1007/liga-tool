"# liga-tool-manager" 
# Install
- Press WINDOW key + R type "cmd" then press ENTER key
- Type two statements :
    ```
    md liga
    cd liga
    git clone https://github.com/ndp1007/liga-tool.git .
    npm run setup
    ```
    
# CLI arguments
    -V, --version             output the version number
    -d, --debug               output extra debugging
    -h, --help                display help for command  
    -awls, --all-whitelabels  sync all Images in WL list
    -wl, --whitelabel <name>  specify name of WL, can use WL1,WL2 to for multiple WLs
       - Sub options of -wl <name>:
            -s, --safe           sync latest Images slowly and safely
            -q, --quick          sync latest Images quickly(is default)
            -sq, --supper-quick  sync latest Images supper quickly (Recommeded using for one WL)
            -www, --www          sync with www url
            -http, --http',      sync with http protocol
            -a, --all            sync all Images
            -f, --from <index>   sync from index of WL list
            -o, --open           open WL's Images folder

# Sample statements
```js
// sync one WL name
node sync -wl HANAHA

//sync WL list
node sync -wl HANAHA,HAHAHA,HABANA,BANANA

// sync WL list from index(start syncing from HABANA)
node sync -wl HANAHA,HAHAHA,HABANA,BANANA -f 2

// sync image from domain include www and open folder
node sync -wl BANANA -www -o 

// sync image by url: http://www. + domain supper quickly then open folder Image too
node sync -wl BANANA -www -http -sp -o 

```
# Knowledge
1. Remove emty folder by recursive algorithm 
    - https://gist.github.com/jakub-g/5903dc7e4028133704a4 normal
    - https://gist.github.com/fixpunkt/fe32afe14fbab99d9feb4e8da7268445 promise

# Change log
All notable changes to this project will be documented in this part.

## [0.3.17]
### Added
- Final Report 
    ```js 
    {
        total: 7,
        latest: [ '5 White Labels' ],
        changed: ['BANANA'],
        error: [ 'HABANA' ] 
    }
    ```
- **-awls**/**--all-whitelabels** option
- Sync all WLs in active WL list from WLs.json (included w3w & www)
- Should add more **--open** option to view ensure image synced then type WL's switching command line.
    ```js
    // implicit option
    node sync -awls
    // explicit option
    node sync --all-whitelabels
    ```
- **-www**/**--www** option : sync with www url'
- **-http/--http** option : sync with http protocol
### Changed
- **hasWww = false** is default

## [0.0.6]
### Fixed bugs 
- Fixed program is stopped by deleting file not found
- Final Report list WLs are updated images to Error list
### Added
- **--sq**/**--supper-quick** option
- Recommended using for sync one WL with empty WL's images folder case
- Should add more **--open** option to view ensure image synced then type WL's switching command line.
    ```js
    // implicit option
    node sync -wl BANANA -sq -o
    // explicit option
    node sync -wl BANANA --supper-quick --open
    ```
## [0.0.5]
### Fixed bugs 
- Uppercase whitelabel name 
### Added
- Final Report
### Changed
- **quick** is default sync, disable quick by add -s/--safe

## [0.0.4]
### Fixed bugs 
- Trim space whitelabel name 
- **--all** option 
- Process bar 
- Remove all empty folders after syncing completed 

### Added
- **deplayTime** prop at switch.cfg
- **showDownloadingFileName** prop at switch.cfg
- **--quick** option 
- Final Report
### Changed
- **quick** is default sync, disable quick by add -s/--safe

## 0.0.1 - 2020-6-1
 - 1st release
