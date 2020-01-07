[Back to README](../README.md)

# xuyan Browser Runtime

You can now run xuyan as normal Javscript script right in your html.

[**Check out the demo**](https://jsfiddle.net/antfu/u532ny49/)

## Installation

Add following script in the `<head>` of your html file.

```html
<script src='https://unpkg.com/@xuyanlang/runtime'></script>
```

That's all, you are good to go!

## Usage

To use xuyan in script, you **HAVE TO** specify `type="application/xuyan"` for the `<script>` tag. For example:

```html
<script type="application/xuyan">
吾有一數。曰三。名之曰「甲」。
為是「甲」遍。
  吾有一言。曰「「問天地好在。」」。書之。
云云。
</script>
```

### Scoped script

By default, all the variables in xuyan will exposed globally. For the previous example, `甲` is accessible by `window.甲`. If you do not want to messed up your globals, you can specify the `scoped` attr.

```html
<script type="application/xuyan" scoped>
吾有一數。曰三。名之曰「甲」。
</script>
```

### Remote scripts

You can import remote scripts as you will do for Javascript.

```html
<script type="application/xuyan" src="https://raw.githubusercontent.com/LingDong-/xuyan-lang/master/examples/fizzbuzz.wy"></script>
```

### Outputing Hanzi

By default, it will convert numbers and bools to hanzi. If you want to output raw numbers, you can specify `outputHanzi="false"` in attr of script tag.

```html
<script type="application/xuyan" outputHanzi="false">
吾有一數。曰三。書之。
</script>
```

### DOM Hacks

There are some hacks you can do to access the DOM and browser APIs. This allows xuyan to do some realworld applications.

```html
<script type="application/xuyan">
施「((title)=>document.title=title)」於「「徐延」」。
施「((text)=>document.body.innerText=text)」於「「問天地好在。」」。
</script>
```
