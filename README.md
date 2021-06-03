# liga-tool

## Install

- Press WINDOW key + R type "cmd" then press ENTER key
- Type two statements :

```js
md liga
cd liga
git clone https://github.com/ndp1007/liga-tool.git .
npm install
node update
```

## liga-copy & check (old commandline)

- Show document by statement :

```js
// short docs
node help c
// full docs
node c help
```

## liga-switch (old commandline)

- Show document by statement :
  
```js
node help s
```

## Remote desktop service

- Use with WLs.Ext.html

```js
// run service by cli
node rdservice
```

## Remote desktop cli
  
```js
// remote to whitelabelname's server
node rd whitelabelname
```

## liga-sync (standard commandline)

## CLI arguments

```cli
-V, --version             output the version number
-d, --debug               output extra debugging
-h, --help                display help for command  
-allwls, --all-whitelabels  sync all Images in WL list
-wl, --whitelabel <name>  specify name of WL, can use WL1,WL2 to for multiple WLs
    - Sub options of -wl <name>:
        -s, --safe           sync latest Images slowly and safely
        -q, --quick          sync latest Images quickly(is default)
        -sq, --supper-quick  sync latest Images supper quickly (Recommeded using for one WL)
        -w, --www            sync with www url
        -http, --http',      sync with http protocol
        -a, --all            sync all Images folder
        -f, --from <index>   sync from index of WL list
        -o, --open           open WL's Images folder
        -l, --log            show log info
        -u, --url            sync with specific domain (only using for one WL and must use with -all option together)
        -ft, --from-test           sync Image from test site
---------------
-dmallwls, --domain-all-wls  sync valid domain of all WLs
-dm, --domain <name>  specify name of WL, can use WL1,WL2 to for multiple WLs
    - Sub options of -dm <name>:
        -dt, --domain-type     sync with domain type, value is "ip" or "name"(as default)
        -st, --site-type       sync with site type, value is "member"(as default), "mobile", "agent"
        -w, --www              sync with www url
        -http, --http',        sync with http protocol
        -l, --log              show log info
        -list, --list-domain   only show domains info
        -ud <domain>, --update-domain  update valid domain by manual specific domain
```

## Common statements

```js
// sync image from test site
node sync -wl HANABA -ft
// or
node sync -wl HANABA --from-test

// sync image of all active white labels list(in WLs.json)
node sync -allwls
// or
node sync --all-whitelabels

// sync image of all active white label list from index 
node sync -allwls -f 15

// sync new wl (whole folder images)
node sync -wl HANABA -sq
// or
node sync -wl HANABA --supper-quick

// sync one WL name
node sync -wl HANAHA

//sync WL list
node sync -wl HANAHA,HAHAHA,HABANA,BANANA

// sync WL list from index(start syncing from HABANA)
node sync -wl HANAHA,HAHAHA,HABANA,BANANA -f 2

// sync image from domain include www and open folder
node sync -wl BANANA -w -o

// sync image by url: http://www. + domain then open folder Image too
node sync -wl BANANA -w -http -o

```

## Tips

### Sync command line of test site

```js
// sync image from test site
node sync -wl BANANA -u bananamain.playplay.com -http -a -sq
// or
node sync -wl BANANA -t
// add some options parameters
// sync images from test site  show log and open folder after synced
node sync -wl BANANA --test --log -o
```

## Change log

***All notable changes to this project will be documented in this part.***
## [0.3.0r316]

### Added

- Add `-ud` option: update valid domain by manual specific domain
- Add `-list` option: only show valid domains, don't update to global
## [0.3.0r309]

### Added

- Add update valid domains to global feature

- Sync domain name of all whitelabel of member, agent, mobile
  - member `node sync -dm <name>` -> sync valid domain one/many whitelabel, name is "HAHAHA" "or HAHAHA, HABANA", file will be saved at  `domains_name_member.json` and update to global valid domains memory
  - member `node sync -dmallwls` -> sync valid domains all whitelabels save to `domains_name_member.json` and update to global valid domains memory

  - agent `node sync -dm habana -st agent` ->  sync valid domain of agent site
  - mobile `node sync -dm bungata -st mobile` -> sync valid domain of mobile site

## [0.1.1r185]

### Changed

- Change ```request``` and ```request-promise``` to ```node-fetch``` because of [deprecated issue](<https://github.com/request/request/issues/3142>)

## [0.1.0r115]

### Added

- Remote desktop service

    ```js
    // run service by cli
    node rdservice
    ```

- Remote desktop cli
  
    ```js
    // remote to whitelabelname's server
    node rd whitelabelname
    ```

## [0.0.9r81]

### Fixed

- Comparing algorithm (Sometime Malaysia team can't sync latest image)
  - Add **timezone** at switch.cfg (default as Malaysia, VN team need set key **timezone :'VN'**
- **url** option missing in case sync only one WL

## [0.0.9r53]

### Added

- Clone Images of WLs
    Copy some images in Images folder of some WLs

## [0.0.8r45]

### Fixed

- sync all white labels list can be use -f option together

    ```js
        // start sycing from white lable has index is 15
        node sync -allwls -f 15
    ```

- get active white labels in json data not plain text
- ~~show error message when required option -wl not specified~~

    ```js
        // need research more this one
        .requiredOption('-wl, --whitelabel name', 'description')

    ```

### Added

- **-u**/**--url** option : sync with specific url, only use for one white label
- **-l**/**--log** option : enable log console
- **-ft**/**--from-test** option : sync image from test site
- ~~**all/all-whitelabel** command : sync all whitelabels~~
- New verisoning system

### Changed

- **awls** to **allwls**

## [0.0.7r18]

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

- **-w**/**--www** option : sync with www url'
- **-http/--http** option : sync with http protocol
  
### Changed

- **hasWww = false** is default

## [0.0.6r17]

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

## [0.0.5r15]

### Fixed bugs

- Uppercase whitelabel name

### Added

- Final Report

### Changed

- **quick** is default sync, disable quick by add -s/--safe

## [0.0.4r10]

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

- **quick** is default sync, disable quick mode by add -s/--safe

## [0.0.1 - 2020-6-1]

- 1st release

############# 0o0 #############
