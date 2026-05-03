#### undefined 返回函数的更简单隐式返回

在早期版本的 TypeScript 中，只有 **`void-`** 和 **`any-`** 返回函数可以不写 `return` 语句，这意味着即使一个函数返回 **`undefined`**，也必须显式写明 `return undefined`。

TypeScript 5.1 允许返回 `undefined` 的函数没有 `return` 语句。

```typescript
//  Works in TypeScript 5.1!
function f4(): undefined {
    // no returns
}

//  Works in TypeScript 5.1!
takesFunction((): undefined => {
    // no returns
});
```



#### Getters 、Setters 不相关类型

 TypeScript 4.3 允许 `getter`、 `setter` 访问器可以指定两种不同的类型，但是 `getter` 类型必须是 `setter` 类型的子类型。 

```typescript
interface Serializer {
    set value(v: string | number | boolean);
    get value(): string;
}

declare let box: Serializer;

// Allows writing a 'boolean'
box.value = true;

// Comes out as a 'string'
console.log(box.value.toUpperCase());
```



TypeScript 5.1 现在允许 `getter` 、`setter` 可以有完全不相关的类型，前提是它们有显式的类型注释。

```typescript
interface CSSStyleRule {
    // ...

    /** Always reads as a `CSSStyleDeclaration` */
    get style(): CSSStyleDeclaration;

    /** Can only write a `string` here. */
    set style(newValue: string);

    // ...
}
```



#### `JSX Elements` 和 `JSX Tag` 类型之间的解耦类型检查

对于 `JSX` 组件而言，会检查是否属于 `JSX.Element` 类型。

但是 `React` 未来版本可能会支持返回 `promise` 的组件，如果不放宽 `JSX.Element` 类型，现有版本的 `TypeScript` 就无法表达这一点。



`TypeScript 5.1` 开始使用 **`JSX.ElementType`** 类型，可以精确指定什么可以作为 `JSX` tag。

 

#### 带名称空间的 `JSX Attributes`

```typescript
import * as React from "react";

// Both of these are equivalent:
const x = <Foo a:b="hello" />;
const y = <Foo a : b="hello" />;

interface FooProps {
    "a:b": string;
}

function Foo(props: FooProps) {
    return <div>{props["a:b"]}</div>;
}
```



带名称空间的 `tag`

```typescript
// In some library's code or in an augmentation of that library:
namespace JSX {
    interface IntrinsicElements {
        ["a:b"]: { prop: string };
    }
}

// In our code:
let x = <a:b prop="hello!" />;
```



原文链接：https://devblogs.microsoft.com/typescript/announcing-typescript-5-1/
