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

---

#### clsx

```json
"tailwindCSS.experimental.classRegex": [
  ["clsx\\(([^)]*)\\)", "(?:'|\"|`)([^']*)(?:'|\"|`)"]
]

# Take note of the outer square brackets!
```

```js
clsx('p-4', 'text-center');
```

---

#### HeadlessUI Transition (React)

```json
"tailwindCSS.experimental.classRegex": [
  "(?:enter|leave)(?:From|To)?=\\s*(?:\"|')([^(?:\"|')]*)"
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

```json
"tailwindCSS.experimental.classRegex": [
  ["classnames\\(([^)]*)\\)", "'([^']*)'"]
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

```json
"tailwindCSS.experimental.classRegex": [
  "tailwind\\('([^)]*)\\')", "(?:'|\"|`)([^']*)(?:'|\"|`)"
]
```

> Note:
> You might have to add "style" to the `Class Attributes` setting of the Tailwind CSS Extension 
> 
> Related: https://github.com/vadimdemedes/tailwind-rn/issues/100#issuecomment-1036813662

```js
"tailwindCSS.experimental.classRegex": [
  tailwind('pt-12 items-center');
]
```

Credits: [tommulkins](https://github.com/tommulkins)

#### cva 

> [class-variance-authority](https://github.com/joe-bell/cva)
```js
"tailwindCSS.experimental.classRegex": [
  ["cva\\(([^)]*)\\)", "[\"'`]([^\"'`]*).*?[\"'`]"]
]

# Take note of the outer square brackets!
```

Credits: [Joe Bell](https://github.com/joe-bell)

#### classList

```js
"tailwindCSS.experimental.classRegex": [
  ["classList={{([^;]*)}}", "\\s*?[\"'`]([^\"'`]*).*?:"]
]

# Take note of the outer square brackets!
```

Credits: [carere](https://github.com/carere)

#### tailwind-join

> [tailwind-join](https://github.com/satelllte/tailwind-join)
```js
"tailwindCSS.experimental.classRegex": [
  ["twJoin\\(([^)]*)\\)", "'([^']*)'"]
]

# Take note of the outer square brackets!
```
Credits: [satelllte](https://github.com/satelllte)
