# GENERAL QUESTIONS
* How can we provide optimal code completion and documentation lookup for a large ES6 library with several modules?

# ISSUES WITH REPRO

1. When actual paths to ES6 modules are used as imports, WebStorm doesn't use documentation provided in a .d.ts anymore. 
**Desired behavior**: possiblity to map modules to typings in WebStorm, so WS can associate types imported from module files with types declared in the typings file ("this is the same library"). Or: WebStorm tries to find this mapping by itself :)
2. Interfaces declared in .d.ts modules not found [Youtrack issue](https://youtrack.jetbrains.com/issue/WEB-30647)
3. JS **and** TypeScript: No documentation found for static interface members
4. TypeScript: WS can't handle "indirection" - "Element is not accessible"
   * [Documentation lookup for imported types doesn't work](https://youtrack.jetbrains.com/issue/WEB-30165) 
   * [Wrong/sub-optimal auto-imports](https://youtrack.jetbrains.com/issue/WEB-30164) 
5. No doc lookup for jsdoc types that are not imported (e.g. `@param {IFoo}`), although it works when the type is imported. Without import, WS can't resolve the amibguity (merge) between var and interface declaration in d.ts, it seems (works when there's only the interface).     
6. Various "Expression type is not assignable to..." problems
   * When using classes or interfaces in @param/@return comments, WS doesn't seem to   consider the referenced types the same as the one used in the comment.
   * Custom classes that extend library types are not recognized as valid assignments to variables/parameter expecting the library type
7. UMD Variant: Class/Constructor documentation not found. Should show constructor documentation
8. Several issues with extended/implemented interfaces 


# OTHER ISSUES
* @links in documentation - almost all links don't work - what should we write there as qualified name? maybe `"sub/module".Type`?
* Documentation lookup: which module does this type belong to? (more important than showing the .d.ts where the documentation was found) 
* [Markdown support](https://youtrack.jetbrains.com/issue/WEB-11052) (WS has only HTML, VSCode has only Markdown)
* Overloads: highlight/select just the chosen one   