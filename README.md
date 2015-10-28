# mkcss.php

CSS file generator(altCSS).
It likes YAML. Easy way to generate CSS.

## Required

PHP 5.3 (tested by PHP 5.5)

# How to use

If you use command, then execute command:

```
$ php mkcss.php test.mkcss
```

If you use browser:

```
http://example.com/mkcss.php?f=test&nocache=1
```

# examples

## Simple example

Simple example source:

```
// simple example
body:
  background-color: black
  color: white

#hoge:
  background-color: white
  color: red

#fuga:
  background-color: blue
  color: white
```

Simple example generated:

```
body { background-color: black; color: white;  }
#hoge { background-color: white; color: red;  }
#fuga { background-color: blue; color: white;  }
```

## Variable

source:

```
$main_color = #ff0000
$sub_color = #ff00ff
$back_color = black

#head:
  background-color: $back_color
  color: $main_color
```
generated:

```
#head { background-color: black; color: #ff0000;  }
```

## Calc parameters

source:

```
body:
  font-size: 1 + 2 * 3 + 4px
```

generated:

```
body { font-size: 11px; }
```

## Mixin

- define: @mixin name(v1:def, v2:def, ...)
- include: @include name(v1, v2, ...)

source:

```
// mixin sample
@mixin set_basic($front, $back):
  background-color: $front
  color: $back

body:
  @include set_basic(black, white)
```

generated:

```
body { background-color: black; color: white;  }
```

## Nested style

source:

```
table:
  border: 1px solid black

  th:
    font-size: 14px
    font-weight: bold

  td:
    font-size: 12px
    background-color: white
```

generated:

```
table { border: 1px solid black; }
table th { font-size: 14px; font-weight: bold; }
table td { font-size: 12px; background-color: white; }
```
