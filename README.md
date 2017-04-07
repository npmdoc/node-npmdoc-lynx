# api documentation for  [lynx (v0.2.0)](https://github.com/dscape/lynx)  [![npm package](https://img.shields.io/npm/v/npmdoc-lynx.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-lynx) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-lynx.svg)](https://travis-ci.org/npmdoc/node-npmdoc-lynx)
#### Minimalistic StatsD client for Node.js programs

[![NPM](https://nodei.co/npm/lynx.png?downloads=true)](https://www.npmjs.com/package/lynx)

[![apidoc](https://npmdoc.github.io/node-npmdoc-lynx/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-lynx_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-lynx/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-lynx/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-lynx/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Lloyd Hilaiel"
    },
    "bugs": {
        "url": "https://github.com/dscape/lynx/issues"
    },
    "contributors": [
        {
            "name": "Nuno Job",
            "email": "nunojobpinto@gmail.com",
            "url": "http://nunojob.com"
        },
        {
            "name": "Mark Bogdanoff",
            "url": "https://github.com/bog"
        }
    ],
    "dependencies": {
        "mersenne": "~0.0.3",
        "statsd-parser": "~0.0.4"
    },
    "description": "Minimalistic StatsD client for Node.js programs",
    "devDependencies": {
        "tap": "~0.3.2"
    },
    "directories": {
        "lib": "./lib/"
    },
    "dist": {
        "shasum": "79e6674530da4183e87953bd686171e070da50b9",
        "tarball": "https://registry.npmjs.org/lynx/-/lynx-0.2.0.tgz"
    },
    "homepage": "https://github.com/dscape/lynx",
    "keywords": [
        "stats",
        "metrics",
        "metricsd",
        "statsd",
        "etsy",
        "statsd client",
        "statsd driver",
        "graphite"
    ],
    "licenses": [
        {
            "type": "MIT",
            "url": "http://github.com/dscape/lynx/raw/master/LICENSE"
        }
    ],
    "main": "./lib/lynx",
    "maintainers": [
        {
            "name": "dscape",
            "email": "nunojobpinto@gmail.com"
        },
        {
            "name": "lloyd",
            "email": "lloyd@hilaiel.com"
        }
    ],
    "name": "lynx",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/dscape/lynx.git"
    },
    "scripts": {
        "test": "tap tests/*-test.js"
    },
    "version": "0.2.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module lynx](#apidoc.module.lynx)
1.  [function <span class="apidocSignatureSpan">lynx.</span>sample (stats, sample_rate)](#apidoc.element.lynx.sample)
1.  [function <span class="apidocSignatureSpan">lynx.</span>super_ ()](#apidoc.element.lynx.super_)



# <a name="apidoc.module.lynx"></a>[module lynx](#apidoc.module.lynx)

#### <a name="apidoc.element.lynx.sample"></a>[function <span class="apidocSignatureSpan">lynx.</span>sample (stats, sample_rate)](#apidoc.element.lynx.sample)
- description and source-code
```javascript
function sample(stats, sample_rate) {
  //
  // If we don't have a sample rate between 0 and 1
  //
  if (typeof sample_rate !== 'number' || sample_rate > 1 || sample_rate < 0) {
    //
    // Had to ignore the invalid sample rate
    // Most of the times this is because sample_rate is undefined
    //
    return stats;
  }

  var sampled_stats = {};

  //
  // Randomly determine if we should sample this specific instance
  //
  if (mt.genrand_real2(0,1) <= sample_rate) {
    //
    // Note: Current implementation either sends all stats for a specific
    //       sample rate or sends none. Makes one wonder if granularity
    //       should be at the individual stat level
    //
    Object.keys(stats).forEach(function construct_sampled(stat) {
      var value = stats[stat];
      sampled_stats[stat] = value + '|@' + sample_rate;
    });
  }

  return sampled_stats;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.lynx.super_"></a>[function <span class="apidocSignatureSpan">lynx.</span>super_ ()](#apidoc.element.lynx.super_)
- description and source-code
```javascript
function Stream() {
  EE.call(this);
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
