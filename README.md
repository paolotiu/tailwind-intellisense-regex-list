## Tailwind Regex List <!-- omit in toc -->

A regex expressions for tailwind intellisense

[Related Issue](https://github.com/tailwindlabs/tailwindcss-intellisense/issues/129)

[Blog Post](https://www.paolotiu.com/blog/get-tailwind-intellisense-anywhere)

### Table of contents <!-- omit in toc -->

- [clsx](#clsx)
- [HeadlessUI Transition (React)](#headlessui-transition-react)
- [classnames](#classnames)
- [Plain Javascript Object](#plain-javascript-object)
- [Nested Object](#nested-object-inside-a-plain-javascript-object)
- [JavaScript string variable](#javascript-string-variable)
- [JavaScript string variable with keywords](#javascript-string-variable-with-keywords)
- [TypeScript or JavaScript variables, strings or arrays with keyword](#typescript-or-javascript-variables-strings-or-arrays-with-keyword)
- [tailwind-rn](#tailwind-rn)
- [cva](#cva)
- [classList](#classlist)
- [tailwind-join](#tailwind-join)
- [tailwind-merge](#tailwind-merge)
- [tailwind-variants](#tailwind-variants)
- [HAML](#haml)
- [JQuery](#jquery)
- [DOM](#dom)
- [Comment Tagging](#comment-tagging)
- [Laravel Blade directives and component attribute functions](#laravel-blade-directives-and-component-attribute-functions)
- [Stimulus CSS Classes](#stimulus-css-classes)
- [Tagged Template Literals](#tagged-template-literals)
- [Literally everywhere](#everywhere)


#### clsx
> [clsx](https://github.com/lukeed/clsx)

```json
"tailwindCSS.experimental.classRegex": [
  ["clsx\\(.*?\\)(?!\\])", "(?:'|\"|`)([^\"'`]*)(?:'|\"|`)"]
]

# Take note of the outer square brackets!
```

```js
clsx('p-4', 'text-center');
```

---

#### HeadlessUI Transition (React)
> [HeadlessUI React](https://headlessui.com/)

```json
"tailwindCSS.experimental.classRegex": [
  "(?:enter|leave)(?:From|To)?=\\s*(?:\"|'|{`)([^(?:\"|'|`})]*)"
 ]
```

```js
<Transition
  enter="transition-opacity duration-75"
  enterFrom="opacity-0"
  enterTo="opacity-100"
  leave="transition-opacity duration-150"
  leaveFrom="opacity-100"
  leaveTo="opacity-0"
>
  I will fade in and out
</Transition>
```

---

#### classnames
> [classnames](https://github.com/JedWatson/classnames)

```json
"tailwindCSS.experimental.classRegex": [
  ["classnames\\(([^)]*)\\)", "[\"'`]([^\"'`]*)[\"'`]"]
]

# Take note of the outer square brackets!
```

```js
classnames('bg-red-500', 'uppercase');
```

Credits: [bradcl](https://github.com/bradlc)

---

#### Plain Javascript Object

```json
"tailwindCSS.experimental.classRegex": [
  ":\\s*?[\"'`]([^\"'`]*).*?,"
]
```

```js
const styles = {
  wrapper: 'flex flex-col',
  navItem: 'relative mb-2 md:mb-0',
  bullet: 'absolute w-2 h-2 2xl:w-4 2xl:h-4 bg-red rounded-full',
};
```

Credits: [michaelschufi](https://github.com/michaelschufi)

---

#### Nested object inside a plain javascript object

```json
"tailwindCSS.experimental.classRegex": [
  [
    "classNames:\\s*{([\\s\\S]*?)}",
    "\\s?[\\w].*:\\s*?[\"'`]([^\"'`]*).*?,?\\s?"
  ]
]
```

```js
const props = {
    classNames: {
      container: "w-full h-full"
   }
}
```

---

#### JavaScript string variable

```json
"tailwindCSS.experimental.classRegex": [
  "(?:const|let|var)\\s+[\\w$_][_\\w\\d]*\\s*=\\s*['\\\"](.*?)['\\\"]"
]
```

```js
const inputClassNames = "scroll-m-0 border-collapse";
```

---

#### JavaScript string variable with keywords

```json
"tailwindCSS.experimental.classRegex": [
  ["(?:\\b(?:const|let|var)\\s+)?[\\w$_]*(?:[Ss]tyles|[Cc]lasses|[Cc]lassnames)[\\w\\d]*\\s*(?:=|\\+=)\\s*['\"]([^'\"]*)['\"]"]
]
```

```js
const styles = "bg-red-500 text-white";
let Classes = "p-4 rounded";
var classnames = "flex justify-center";
const buttonStyles = "bg-blue-500 hover:bg-blue-700";
let formClasses = "space-y-4";
var inputClassnames = "border-2 border-gray-300";
styles += 'rounded';
```

Credits: [mxmalykhin](https://github.com/mxmalykhin)

---

#### TypeScript or JavaScript variables, strings or arrays with keyword

Captures Tailwind classes based on the following patterns:

- variables ending with a "Styles" suffix and with or without TS types.
- classes within single quotes, double quotes, or backticks
- classes within strings or arrays

> Edit Styles keyword to target different variable names/suffixes
```json
"tailwindCSS.experimental.classRegex": [
  ["Styles\\s*(?::\\s*[^=]+)?\\s*=\\s*([^;]*);", "['\"`]([^'\"`]*)['\"`]"]
]
```

Examples:

```ts
const variableStyles: (string | undefined)[] = [
  className,
  showCaret ? 'pr-1' : '',
  icon ? 'px-1.5 py-0.5' : 'px-3 py-1',
];
```

```js
const baseStyles = `items-center flex p-5 mx-2 my-1`;
```
Credits: [avgvstvs96](https://github.com/avgvstvs96)

---


#### tailwind-rn
> [tailwind-rn](https://github.com/vadimdemedes/tailwind-rn)
```json
"tailwindCSS.experimental.classRegex": [
  "tailwind\\('([^)]*)\\')", "(?:'|\"|`)([^\"'`]*)(?:'|\"|`)"
]
```

> Note:
> You might have to add "style" to the `Class Attributes` setting of the Tailwind CSS Extension 
> 
> Related: https://github.com/vadimdemedes/tailwind-rn/issues/100#issuecomment-1036813662

```js
tailwind('pt-12 items-center');
```

Credits: [tommulkins](https://github.com/tommulkins)

#### cva 

> [class-variance-authority](https://github.com/joe-bell/cva)

```json
"tailwindCSS.experimental.classRegex": [
  ["cva\\(([^)]*)\\)", "[\"'`]([^\"'`]*).*?[\"'`]"]
]

# Take note of the outer square brackets!
```

```js
cva("rounded", {
  variants: {
    size: {
      sm: "p-4",
      md: "p-6"
    }
  }
})
```

Credits: [Joe Bell](https://github.com/joe-bell)

#### classList

```json
"tailwindCSS.experimental.classRegex": [
  ["classList={{([^;]*)}}", "\\s*?[\"'`]([^\"'`]*).*?:"]
]

# Take note of the outer square brackets!
```


Credits: [carere](https://github.com/carere)

#### tailwind-join

> [tailwind-join](https://github.com/satelllte/tailwind-join)

```json
"tailwindCSS.experimental.classRegex": [
  ["twJoin\\(([^)]*)\\)", "[\"'`]([^\"'`]*)[\"'`]"]
]

# Take note of the outer square brackets!
```
Credits: [satelllte](https://github.com/satelllte)

#### tailwind-merge
> [tailwind-merge]

```json
"tailwindCSS.experimental.classRegex": [
    ["(?:twMerge|twJoin)\\(([^;]*)[\\);]", "[`'\"`]([^'\"`;]*)[`'\"`]"]
]        
```

```js
twMerge('p-8 rounded bg-slate-500', 'pt-10 bg-slate-800')
```
Credits: [bradennapier](https://github.com/bradennapier)

#### tailwind-variants
```json
"tailwindCSS.experimental.classRegex": [
  ["tv\\(([^)]*)\\)", "{?\\s?[\\w].*:\\s*?[\"'`]([^\"'`]*).*?,?\\s?}?"]
]

# Take note of the outer square brackets!
```

```js
tv({
  base: 'bg-gray-500 grid grid-cols-1 gap-0 tablet:grid-cols-2 mx-auto my-0 p-0 w-full',
  variants: {
    threeColumn: {
      true: 'three-column grid-cols-3 tablet:grid-cols-3 mb-2'
    },
    twoColumn: {
      true: 'grid-cols-2'
    }
  }
})
```

Credits: [magicink](https://github.com/magicink)

#### HAML
> [HAML]

```json
"tailwindCSS.experimental.classRegex": [
  [ "class: ?\"([^\"]*)\"", "([a-zA-Z0-9\\-:]+)" ],
  [ "(\\.[\\w\\-.]+)[\\n\\=\\{\\s]", "([\\w\\-]+)" ],
]

# Take note of the outer square brackets!
```

``` haml
 %section.text-right.uppercase.font-extralight{class: "leading-[1.1rem]"} lorem
```

Credits: [S1M1S](https://github.com/S1M1S)

#### JQuery

```json
"tailwindCSS.experimental.classRegex": [
  ["(?:add|remove)Class\\(([^)]*)\\)", "(?:'|\"|`)([^\"'`]*)(?:'|\"|`)"]
]

# Take note of the outer square brackets!
```

```js
$('body').addClass('bg-red-500');
$('body').removeClass('bg-red-500');
```

Credits: [alexvipond](https://gitbub.com/alexvipond)

#### DOM

```json
"tailwindCSS.experimental.classRegex": [
  ["classList.(?:add|remove|toggle)\\(([^)]*)\\)", "(?:'|\"|`)([^\"'`]*)(?:'|\"|`)"]
]

# Take note of the outer square brackets!
```

```js
document.body.classList.add('bg-red-500');
document.body.classList.remove('bg-red-500');
document.body.classList.toggle('hidden');
```

Credits: [alexvipond](https://gitbub.com/alexvipond)

```json
"tailwindCSS.experimental.classRegex": [
  ["\\s*.className\\s*=\\s*['\\\"](.*?)['\\\"]"]
]

# Take note of the outer square brackets!
```

```js
document.body.className = 'bg-red-500';
yourCustumEl.className = 'bg-red-500';
```

Credits: [dennisdotg](https://gitbub.com/dennisdotg)

#### Comment Tagging
```json
"tailwindCSS.experimental.classRegex": [
  "@tw\\s\\*\/\\s+[\"'`]([^\"'`]*)"
]
```

```js
/** @tw */ "px-5 text-center bg-white py-16 &:not[hidden]"
```

Credits: [james2doyle](https://github.com/james2doyle)

#### Laravel Blade directives and component attribute functions

> [Laravel Blade Templates](https://laravel.com/docs/10.x/blade)

```json
"tailwindCSS.experimental.classRegex": [
  ["@?class\\(([^)]*)\\)", "['|\"]([^'\"]*)['|\"]"],
  "(?:\"|')class(?:\"|')[\\s]*=>[\\s]*(?:\"|')([^\"']*)"
]
```

```php
@class(['bg-red-500', 'text-white'])
$attributes->class(['bg-red-500', 'text-white'])
$attributes->merge(['class' => 'bg-red-500 text-white'])
```

Credits: [czernika](https://github.com/czernika) and [Nicholas Davidson](https://github.com/ndavidson7)

#### Stimulus CSS Classes
> [Stimulus CSS Classes](https://stimulus.hotwired.dev/reference/css-classes)

```json
"tailwindCSS.experimental.classRegex": [
  ["data-.*-class=['\"]([^'\"]*)"]
]
```

```html
<form data-controller="search"
      data-search-loading-class="bg-gray-500 animate-spinner cursor-busy">
  <input data-action="search#loadResults">
</form>
```

#### Tagged Template Literals

```json
"tailwindCSS.experimental.classRegex": [
  [
    "(tw`(?:(?:(?:[^`]*\\$\\{[^]*?\\})[^`]*)+|[^`]*`))",
    "((?:(?<=`)(?:[^\"'`]*)(?=\\${|`))|(?:(?<=\\})(?:[^\"'`]*)(?=\\${))|(?:(?<=\\})(?:[^\"'`]*)(?=`))|(?:(?<=')(?:[^\"'`]*)(?='))|(?:(?<=\")(?:[^\"'`]*)(?=\"))|(?:(?<=`)(?:[^\"'`]*)(?=`)))"
  ],
]
```

```js
tw`bg-black ${ok ? 'text-white' : `text-red-500 ${errorClassName}`} ${className}`
```

Credits: [sxxov](https://github.com/sxxov)

## EVERYWHERE!!!
For those who are just looking for a quick fix and want to enable tailwind intellisense everywhere.

```json
"tailwindCSS.experimental.classRegex": [
  "([a-zA-Z0-9\\-:]+)"
]
```
```js
pt-1
"pt-1"
const x = "pt-1"
// Will literally trigger everywhere
```
> Note:
> The intellisense for tailwind will show up everytime you type a letter, so it might get annoying.
> Only use this if you are 100% sure!
>
> **Create an issue if you are trying to find a regex to match a certain pattern**

Credits: [Elbasel](https://github.com/Elbasel)
