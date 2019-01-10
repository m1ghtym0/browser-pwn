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

[Source](https://cs.chromium.org/chromium/src/v8/src/)

[Build](https://v8.dev/docs/build)


Build (Ubuntu 18.04):

```
$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
$ export PATH=$PATH:./depot_tools
$ gclient
$ mkdir ./v8 && cd ./v8
$ fetch v8 && cd v8
$ git pull
$ gclient sync
$ ./build/install-build-deps.sh
$ tools/dev/gm.py x64.release
$ out/x64.release/d8
```

### TurboFan (V8-JIT Compiler)

[Docs](https://v8.dev/docs/turbofan)

[Blog](https://v8.dev/blog/turbofan-jit)

[Turbolizer (Visualization)](https://github.com/v8/v8/tree/master/tools/turbolizer)



## Firefox (Gecko)

[Project](https://developer.mozilla.org/en-US/docs/Mozilla/Gecko)

[GitHub](https://github.com/mozilla/gecko-dev)


The JavaScript-Engine of Gecko is Spidermonkey.

### Spidermonkey

[Project](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey)

[Source](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey/Getting_SpiderMonkey_source_code)

[Build](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey/Build_Documentation)

Build (Ubuntu 18.04):

```
$ wget -O bootstrap.py https://hg.mozilla.org/mozilla-central/raw-file/default/python/mozboot/bin/bootstrap.py && python bootstrap.py
$ git clone https://github.com/mozilla/gecko-dev.git && cd gecko-dev
$ cd js/src
$ autoconf2.13

# This name should end with "_DBG.OBJ" to make the version control system ignore it.
$ mkdir build_DBG.OBJ
$ cd build_DBG.OBJ
$ ../configure --enable-debug --disable-optimize
# Use "mozmake" on Windows
$ make -j 6
$ js/src/js
```

### IonMonkey (Spidermonkey-JIT Compiler)

[Project](https://wiki.mozilla.org/IonMonkey)

[IonGraph (Visualization](https://github.com/sstangl/iongraph)


## Safari (Webkit)

[Project](https://webkit.org/)

[GitHub](https://github.com/WebKit/webkit)


The JavaScript-Engine of Webkit is JavaScriptCore (JSC).

### JavaScriptCore

[Project](https://developer.apple.com/documentation/javascriptcore)

[Wiki](https://trac.webkit.org/wiki/JavaScriptCore)

[Source](https://github.com/WebKit/webkit/tree/master/Source/JavaScriptCore)


Build (Ubuntu 18.04):

```
$ sudo apt install libicu-dev python ruby bison flex cmake build-essential ninja-build git gperf
$ git clone git://git.webkit.org/WebKit.git && cd WebKit
$ Tools/Scripts/build-webkit --jsc-only
$ cd WebKitBuild/Release
$ LD_LIBRARY_PATH=./lib bin/jsc
```

### FTL JIT (WebKit-JIT Compiler)

[Introduction to Webkit's JavaScript JIT Optimizations](https://webkit.org/blog/3362/introducing-the-webkit-ftl-jit/)

[Introducing the B3 JIT Compiler](https://webkit.org/blog/5852/introducing-the-b3-jit-compiler/)





## Edge (Blink/EdgeHTML)

[Project](https://www.microsoft.com/en-us/windows/microsoft-edge)

[GitHub](https://github.com/MicrosoftEdge)


Since Edge switch to Blink and the Chromium Project as its Rendering-Engine, Edge is using v8 for its JavaScript-Engine as well.
Originally, Edge had is own Rendering-Engine called EdgeHTML, which used the ChakraCore JavaScript-Engine.

## ChakraCore


[GitHub](https://github.com/Microsoft/ChakraCore)

[Build](https://github.com/Microsoft/ChakraCore/wiki/Building-ChakraCore#linux)

Build (Ubuntu 16.04):

```
# To build ChakraCore on Linux: (requires Clang 3.7+ and Python 2)
$ apt-get install -y git build-essential cmake clang libicu-dev libunwind8-dev
$ git clone https://github.com/Microsoft/ChakraCore && cd ChakraCore
$ ./build.sh --cc=/usr/bin/clang-3.9 --cxx=/usr/bin/clang++-3.9 --arch=amd64 --debug
$ out/Debug/ch
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
    * 35c3 FunFox
        *   [Sources](https://github.com/bkth/35c3ctf/tree/master/funfox) 
* v8
    * 34c3: v9
        *   [Sources](https://github.com/saelo/v9)
        *   [WriteUp](https://gist.github.com/itsZN/9ae6417129c6658130a898cdaba8d76c) (Exploit-Script)
    * 35c3: Krautflare
        *   [Files](https://abiondo.me/assets/ctf/35c3/krautflare-33ce1021f2353607a9d4cc0af02b0b28.tar)
        *   [WriteUp](https://abiondo.me/2019/01/02/exploiting-math-expm1-v8/)
        *   [WriteUp](https://www.jaybosamiya.com/blog/2019/01/02/krautflare/)
* Webkit
    *   RealWorldCTF 2018: Engine for Neophytes
        *   [Files](http://mightym0.de/ctf/rwctf-2018/allForPlayers.zip)
    *   35c3: WebKid
        *   [Sources](https://github.com/saelo/35c3ctf/tree/master/WebKid)
        *   [WriteUp](https://github.com/LinusHenze/35C3_Writeups/tree/master/WebKid)
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