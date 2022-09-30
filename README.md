# Converting common TS constructs to Flow

A very incomplete guide of going from TypeScript to Flow. Not sure why you would do this unless you work at Meta 😅 . Otherwise, you probably want to go from flow to TS.  

Try the two here: 
- [Flow playground](https://flow.org/try)
- [TS playground](https://www.typescriptlang.org/play)

Another (out of date) reference: https://github.com/niieani/typescript-vs-flowtype

All examples show TS first, then Flow.

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

### nullable/maybe types
This is actually sort of a sore spot in TS. If you have `strictNullChecks` on (recommended), it can make sense to have a global type that looks like this: 
```ts
type Nullable<T> = T | undefined | null;
```
In flow, this concept is built-in with the `?` prefix operator.
```js
?string
```

### Partial<T>
In flow, `$Shape` is equivalent to `Partial`.
```ts
type Obj = { id: number, name: string };
Partial<Obj>
```

```js
type Obj = { id: number, name: string };
$Shape<Obj>
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
