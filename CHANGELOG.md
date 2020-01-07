# v0.2.1

## Static Type Inference

When the option is turned on, the compiler will now raise exceptions if your code does not typecheck. Also it is capable of producing type signatures for inspection, e.g. ./example/quicksort.wy produces the following:

```
[0-347] {
  快排 : (('a) arr) -> (('a) arr)
  己 : (num) arr
  [33-285] {
    首 : ('a) arr
    頷 : ('a) arr
    尾 : ('a) arr
    甲一 : 'a
    甲餘 : ('a) arr
    乙 : ('a) arr
    [136-201] {
      丁 : 'a
    }
  }
}
```

For more detail, please refer to #486 

### Standard Library

- Fundamental Calendar library (PR #466, thanks @statementreply), check out [Standard Library cheatsheet](https://github.com/LingDong-/wenyan-lang/blob/master/documentation/Standard-Lib.md) for more details.

### 3rd Party Compilers

- [JVM compiler](https://github.com/MagicLu550/wenyan-lang_jvm) by [MagicLu550](https://github.com/MagicLu550)

### Fixes

- Stdlib was not bundled correctly. (PR #481, thanks @antfu)


# v0.2.0

## ⚠ BREAKING CHANGE: `compile` API change
The first argument lang move to option, please switch to new API.

```js
//before
compile('js', source, { ... })
// after
compile(source, { lang: 'js', ... })
```

The old API is still functional for temporary backward compatible, the support **will be REMOVED in the next minor update.**

## xuyan Snippets Site, #459

Please do check it out. Any feedbacks are welcome!

![](https://user-images.githubusercontent.com/7929704/71650125-049f4800-2ce2-11ea-9f44-31c9b7e626d7.png)

## New Execute API
Check out [API Document](https://github.com/dtsdao/xuyan-lang/blob/master/documentation/Compiler-API.md) and #473


### Fixes
- Fix compiler crash with 0-argument macros (PR #453, thanks @statementreply)
- stdlib: Improve sin, cos and tan (^/1/3) (PR #457, thanks @statementreply)
- bool2hanzi (PR #465, thanks @Fros1er)

### Docs
- Auto generates examples for README.md (PR #448, thanks @cuixiping)


# v0.1.3

## Macros (Experimental)

As you might (not) have noticed, *xuyan-lang* strives to be more readable (for ancient Chinese people). **Macros** provide syntactic sugars to bring the 文采 of your code to the next level.

E.g. Now you can patch xuyan-lang's notorius print function like so:

```
或云「「書「甲」焉」」。
蓋謂「「吾有一言。曰「甲」。書之」」。

書「「問天地好在」」焉。
```

Since we're beating JavaScript to macros, here is a rough C equivalence:

```
#define   書(甲)焉   吾有一言。曰甲。書之
書("問天地好在")焉。
```

See [**Full Documation**](https://github.com/dtsdao/xuyan-lang/blob/master/documentation/Macros.md), #440 for more details.

### Standard Library
A new standard library `畫譜` that manipulates canvas on web pages. Check out the demo on Online IDE!

### Browser Runtime
New package [`@xuyanlang/runtime`](https://github.com/dtsdao/xuyan-lang/blob/master/documentation/Runtime.md) allowing you to run xuyan direct in `<script>` tag of html! (PR #433, thanks @antfu)

### Docs
- [**Standard library document**](https://github.com/dtsdao/xuyan-lang/blob/master/documentation/Standard-Lib.md) added. (PR #432, thanks @antfu @statementreply)

### Examples
- New example 劉徽割圓術 (PR #431, thanks @cuixiping)

### Testing
- More testing cases for hanzi2num added (PR #442, thanks @kaiyuan01)


# v0.1.2

## Overhauled `hanzi2num` (PR #413, thanks [@statementreply](https://github.com/statementreply))
- `塵埃渺漠` are now 10x each
- The character for 10^28 is changed to `穰` (U+7A70).
- `一百一` = 101 now
- Multi-character multipliers are no longer supported.
- Omitting `一` before fractional multipliers is no longer allowed. It's unclear whether `五毫絲` means 0.0051 or 5e-7, so I just disallowed it for now.
- Allow multiple multipliers: `一萬萬` = 1e+8, `一百絲` = 0.01.
- Add support for positional notation: `一三三七` = 1337
- Add digit zero `〇` (exactly one digit of zero) and decimal separator `·`: `三五〇〇·〇一` = 3500.01
- "又" can be used at more places: 三十又六 = 36

### New Features
- `『』` is now supported as string literals, an alternate of `「「」」` (5f698df434133d12b7c6027a197db634b91ace53), resolves #81 
- `、` is now supported sentence separators. (5f698df434133d12b7c6027a197db634b91ace53), resolves #15, resolves #129, resolves #348
- Platform-specific stdlib steup (1cecae9de1919486f34241f379248ed402b4fa96)
- Changelog added

### Fixes
- Nest comments (32b0f3abd1beb55cd28c369ad74b79e677248cc7) resolves #403
- Stdlib: Implement correctly rounded sqrt (4/4/4), (PR #424, thanks [@statementreply](https://github.com/statementreply))

### Examples
- New example "DrawHeart" (PR #410, thanks [@BHMulberry](https://github.com/BHMulberry))