Browser-Pwning Nexus
===

The world of Browsers is dominated by 4 major players:
*   Chromium/Chrome
*   Firefox
*   Safari
*   Edge

The focus for this nexus on Browser-Exploitation is their particular Rendering-Engine:
*   Chromium/Chrome:
    *   Blink
*   Firefox
    *   Gecko   
*   Safari
    *   WebKit  
*   Edge
    *   Blink (former EdgeHTML)



## Chromium (Blink)

[Project](https://www.chromium.org/blink)

[GitHub](https://github.com/chromium/chromium)

[What is Chromium? (DE)](https://www.heise.de/newsticker/meldung/Chrome-und-Chromium-Was-sind-eigentlich-die-Unterschiede-4245456.html)

The JavaScript-Engine of Blink is V8.

### V8

[Project](https://v8.dev/)

[GitHub](https://github.com/v8/v8)

[Build](https://v8.dev/docs/build)


Build:

```
$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
$ export PATH=$PATH:./depot_tools
$ gclient
$ mkdir ./v8 && cd ./v8
$ fetch v8
$ git pull
$ gclient sync
$ ./build/install-build-deps.sh
$ tools/dev/gm.py x64.release
```




## Firefox (Gecko)

[Project](https://developer.mozilla.org/en-US/docs/Mozilla/Gecko)

[GitHub](https://github.com/mozilla/gecko-dev)


The JavaScript-Engine of Gecko is Spidermonkey.

### Spidermonkey

[Project](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey)

[Source](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey/Getting_SpiderMonkey_source_code)

[Build](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey/Build_Documentation)

Build:

```
$ git clone https://github.com/mozilla/gecko-dev.git && cd gecko-dev
$ cd js/src
$ autoconf-2.13

# This name should end with "_DBG.OBJ" to make the version control system ignore it.
$ mkdir build_DBG.OBJ
$ cd build_DBG.OBJ
$ ../configure --enable-debug --disable-optimize
# Use "mozmake" on Windows
$ make
```


## Safari (Webkit)

[Project](https://webkit.org/)

[GitHub](https://github.com/WebKit/webkit)


The JavaScript-Engine of Webkit is JavaScriptCore (JSC).

### JavaScriptCore

[Project](https://developer.apple.com/documentation/javascriptcore)

[Wiki](https://trac.webkit.org/wiki/JavaScriptCore)

[Source](https://github.com/WebKit/webkit/tree/master/Source/JavaScriptCore)

Introduction to Webkit's JavaScript JIT Optimizations: https://webkit.org/blog/3362/introducing-the-webkit-ftl-jit/

Build:

```
$ sudo apt install libicu-dev python ruby bison flex cmake build-essential ninja-build git gperf
$ git clone git://git.webkit.org/WebKit.git && cd WebKit
$ Tools/Scripts/build-webkit --jsc-only
```




## Edge (Blink/EdgeHTML)

[Project](https://www.microsoft.com/en-us/windows/microsoft-edge)

[GitHub](https://github.com/MicrosoftEdge)


Since Edge switch to Blink and the Chromium Project as its Rendering-Engine, Edge is using v8 for its JavaScript-Engine as well.
Originally, Edge had is own Rendering-Engine called EdgeHTML, which used the ChakraCore JavaScript-Engine.

## ChakraCore


[GitHub](https://github.com/Microsoft/ChakraCore)

[Build](https://github.com/Microsoft/ChakraCore/wiki/Building-ChakraCore#linux)

Build:

```
$ apt-get install -y git build-essential cmake clang libicu-dev libunwind8-dev
$ git clone https://github.com/Microsoft/ChakraCore && cd ChakraCore
$ ./build.sh --debug
```

## Resources

* [Javascript Engine Fundamentals](https://mathiasbynens.be/notes/shapes-ics)
* Saelo's phrack article on [Attacking JavaScript-Engines](http://www.phrack.org/papers/attacking_javascript_engines.html)
* [Awesome-Browser-Exploitation](https://github.com/Escapingbug/awesome-browser-exploit)
* [Attacking WebKit applications (Slides)](https://cansecwest.com/slides/2015/Liang_CanSecWest2015.pdf)
* Saelo's JIT-Talk BlackHat 2018
    * [Video](https://youtu.be/emt1yf2Fg9g)
    * [Slides](https://saelo.github.io/presentations/bits_of_launchd.pdf)


## CTF-Challenges

* Spidermonkey
    * 33c3: Feuerfuchs
        *   [Sources](https://github.com/saelo/feuerfuchs)
        *   [WriteUp](https://bruce30262.github.io/Learning-browser-exploitation-via-33C3-CTF-feuerfuchs-challenge/)
    *   Blaze 2018: blazefox
        *   [Sources](https://ctftime.org/task/6000)
        *   [WriteUp](https://devcraft.io/2018/04/27/blazefox-blaze-ctf-2018.html)
        *   [WriteUp](https://gist.github.com/niklasb/4bddc9e8f32c3bd277ed26d66d488834) (Exploit-Script)
        *   [WriteUp](https://github.com/Jinmo/ctfs/blob/master/2018/blaze/pwn/blazefox.html) (Exploit-SCript)
* v8
    * 34c3: v9
        *   [Sources](https://github.com/saelo/v9)
        *   [WriteUp](https://gist.github.com/itsZN/9ae6417129c6658130a898cdaba8d76c) (Exploit-Script)
* ChakraCore
    * Plaid 2017: chakrazy
        *   [WriteUp](https://bruce30262.github.io/Chakrazy-exploiting-type-confusion-bug-in-ChakraCore/)

## RealWorld Write-Ups:

* https://saelo.github.io/posts/firefox-script-loader-overflow.html
* https://saelo.github.io/posts/jsc-typedarray.slice-infoleak.html
* [MobilePwn2Own 2013 - Chrome on Android](https://docs.google.com/document/d/1tHElG04AJR5OR2Ex-m_Jsmc8S5fAbRB3s4RmTG_PFnw/edit)
* https://halbecaf.com/2017/05/24/exploiting-a-v8-oob-write/

 
## JavaScript Resources

* [Types&Values](http://www.ecma-international.org/ecma-262/6.0/#sec-ecmascript-data-types-and-values)
* [Objects](http://www.ecma-international.org/ecma-262/6.0/#sec-objects)
* [Objec-Properties](https://tc39.github.io/ecma262/#sec-property-attributes)