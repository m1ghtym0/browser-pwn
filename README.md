Browser Pwning Nexus
===

The world of Browsers is dominated by 4 major players:
*   Chromium/Chrome
*   Firefox
*   Safari
*   Edge

The core-part for Browser-Exploitation is their particular Rendering-Engine:
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

The JavaScript-Interpreter of Blink is V8.

### V8

[Project](https://v8.dev/)

[GitHub](https://github.com/v8/v8)




## Firefox (Gecko)

[Project](https://developer.mozilla.org/en-US/docs/Mozilla/Gecko)

[GitHub](https://github.com/mozilla/gecko-dev)


The JavaScript-Interpreter of Gecko is Spidermonkey.

### Spidermonkey

[Project](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey)

[Source](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey/Getting_SpiderMonkey_source_code)




## Safari (Webkit)

[Project](https://webkit.org/)

[GitHub](https://github.com/WebKit/webkit)


The JavaScript-Interpreter of Webkit is JavaScriptCore (JSC).

### JavaScriptCore

[Project](https://developer.apple.com/documentation/javascriptcore)

[Source](https://github.com/WebKit/webkit/tree/master/Source/JavaScriptCore)




## Edge (Blink/EdgeHTML)

[Project](https://www.microsoft.com/en-us/windows/microsoft-edge)

[GitHub](https://github.com/MicrosoftEdge)


Since Edge switch to Blink and the Chromium Project as its Rendering-Engine, Edge is using v8 for its JavaScript-Interpreter as well.
Originally, Edge had is own Rendering-Engine called EdgeHTML, which used the ChakraCore JavaScript-Interpreter.

## ChakraCore


[GitHub](https://github.com/Microsoft/ChakraCore)


## Resources

* Saelo's phrack article on [Attacking JavaScript-Engines](http://www.phrack.org/papers/attacking_javascript_engines.html)


## Challenges

* 33c3 Feuerfuchs
    *   [Sources](https://github.com/saelo/feuerfuchs)
    *   [WrteUp](https://bruce30262.github.io/Learning-browser-exploitation-via-33C3-CTF-feuerfuchs-challenge/)
