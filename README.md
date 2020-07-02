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
# Change logs
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
    ```js
    // implicit option
    node sync -awls
    // explicit option
    node sync --all-whitelabels
    ```
- **--sq**/**--supper-quick** option
- **-www**/**--www** option : sync with www url'
- **-http/--http** option : sync with http protocol
- **-a/--all** option : sync all images of WL again
### Changed
- **hasWww = false** is default
- **quick** is default sync, disable quick mode by add -s/--safe

### Fixed bugs 
- Trim space & uppercase whitelabel name 
- Process bar 
- Remove all empty folders after syncing completed 

#2020-6-1
 - 1st release
