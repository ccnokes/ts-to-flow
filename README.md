# Converting common TS constructs to Flow

Try the two here: 
- [Flow playground](https://flow.org/try)
- [TS playground](https://www.typescriptlang.org/play)

Another (out of date) reference: https://github.com/niieani/typescript-vs-flowtype

## General

### typeof
Usage is same in the two.

### keyof 
```ts
type Obj = {
  a: 123
}
type keys = keyof Obj;
```

```js
type Obj = {
  a: 123
}
$Keys<Obj>
```

## Built-ins

### Record 
```ts
Record<string, string | null>
```
There's no built-in for this in flow.
```js
{[key: string]: ?string}
```


## React

### ComponentProps
```tsx
React.ComponentProps<typeof MyComponent>['propName']
```

```js
React.ElementProps<typeof MyComponent>['propName']
```
