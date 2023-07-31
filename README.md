## Tailwind Regex List <!-- omit in toc -->

A regex expressions for tailwind intellisense

[Related Issue](https://github.com/tailwindlabs/tailwindcss-intellisense/issues/129)

[Blog Post](https://www.paolotiu.com/blog/get-tailwind-intellisense-anywhere)

### Table of contents <!-- omit in toc -->

- [clsx](#clsx)
- [HeadlessUI Transition (React)](#headlessui-transition-react)
- [classnames](#classnames)
- [Plain Javascript Object](#plain-javascript-object)
- [tailwind-rn](#tailwind-rn)
- [cva](#cva)
- [classList](#classlist)
- [tailwind-join](#tailwind-join)
- [tailwind-merge](#tailwind-merge)
- [HAML](#haml)
- [Literally everywhere](#everywhere)


#### clsx
> [clsx](https://github.com/lukeed/clsx)

```json
"tailwindCSS.experimental.classRegex": [
  ["clsx\\(([^)]*)\\)", "(?:'|\"|`)([^\"'`]*)(?:'|\"|`)"]
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
  ["(?:twMerge|twJoin)\\(([^\\);]*)[\\);]", "[`'\"`]([^'\"`,;]*)[`'\"`]"]
]        
```

```js
twMerge('p-8 rounded bg-slate-500', 'pt-10 bg-slate-800')
```
Credits: [bradennapier](https://github.com/bradennapier)

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
