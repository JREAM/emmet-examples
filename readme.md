# Emmet Examples

Emmet is for quickly writing HTML and CSS. I'll be using SublimeText 3, but it's available
nearly everywhere.

- First, Install the `emmet` plugin.
- You may or may not have to restart your editor (in ST3 I do).

# How to Use
Type a string of syntax and hit `<tab>` at the end to complete it.
Please note that Sometimes your AutoComplete `<tab>` can cause problems so it might
help to change the hotkey for Emmet.

- When you create items use <tab> to navigate into the elements

# Syntax
Basic Syntax
```
element > nested-element * how-many-nested
element > nested-element.classname * how-many-nested
```

# Structure Syntax
```
; This will place groups in te same level rather than nesting
; by using (group) + (group)
(element > nexted-element * how-many-nested) + (element > nested-element * how-many-nested)
```

# HTML Examples

```
ul>li*5
```

```html
<ul>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

### Add Classes and IDs
```
ul>li.item
```

```html
<ul>
  <li class="item"></li>
</ul>
```

```
ul#mylist>li
```

```html
<ul id="mylist">
  <li></li>
</ul>
```

### Add Auto Incrementing Items
```
; The $ represents an Integer
ul>li.item-$*10>a
```

```html
<ul>
  <li class="item-1"><a href=""></a></li>
  <li class="item-2"><a href=""></a></li>
  <li class="item-3"><a href=""></a></li>
  <li class="item-4"><a href=""></a></li>
  <li class="item-5"><a href=""></a></li>
  <li class="item-6"><a href=""></a></li>
  <li class="item-7"><a href=""></a></li>
  <li class="item-8"><a href=""></a></li>
  <li class="item-9"><a href=""></a></li>
  <li class="item-10"><a href=""></a></li>
</ul>
```

### Add Auto Incrementing Items with Numeric Padding
```
; The $$$ represents an integer, but will be used to pad with 0's if it is below 100

ul>li.item-$$$*10>a
```

```html
<ul>
  <li class="item-001"><a href=""></a></li>
  <li class="item-002"><a href=""></a></li>
  <li class="item-003"><a href=""></a></li>
  <li class="item-004"><a href=""></a></li>
  <li class="item-005"><a href=""></a></li>
  <li class="item-006"><a href=""></a></li>
  <li class="item-007"><a href=""></a></li>
  <li class="item-008"><a href=""></a></li>
  <li class="item-009"><a href=""></a></li>
  <li class="item-010"><a href=""></a></li>
</ul>
```

### Place Items Side by Side
Use the Plus Syntax +

```
div.container>div.sidebar+div.content
```

```html
<div class="container">
  <div class="sidebar"></div>
  <div class="content"></div>
</div>
```

Sometimes the Nesting doesn't go how we want, see below.

```
div.nav>ul>li*3+div.below-nav>h1.page-title

; Since the above nests ul>li and +div, it places it in the LI,
; So we can use Groups!
```

```html
<div class="nav">
  <ul>
    <li></li>
    <li></li>
    <li></li>
    <div class="below-nav">  &lt;-- Sometimes we don't want that.
      <h1 class="page-title"></h1>
    </div>
  </ul>
</div>
```

### Place side by Side Items and Use Groups to Nest
With Groups you wrap items in parentheses. The above code can easily be fixed with grouping:

```
div.nav>ul>li*3+div.below-nav>h1.page-title

; To Groups:

(div.nav>ul>li*3)+(div.below-nav>h1.page-title)
```

```html
<div class="nav">
  <ul>
    <li></li>
    <li></li>
    <li></li>
  </ul>
</div>
<div class="below-nav">
  <h1 class="page-title"></h1>
</div>
```

Example of making a basic html page
```
(html)>(head>(title)+(meta)+(link))>body
```

```html
<html></html>
<head>
  <title></title>
  <meta>
  <link rel="stylesheet" href="">
</head>
<body>
</body>
```

### Create a Page Structure With Groups, Nesting and SideBySide

Since this one is a bit more complicated, first see the tree structure rather than one line to
give you an idea of what we are making.

```
(
  header >
    nav >
      ul >
        li.items *2 >
          a
          a
)
  +
(
  div.container >
    (
      div.sidebar >
    )
      +
    (
      div.content >
    )
)
  +
(
  footer >
    p.muted
)
```

The code Above would read and product like below:

```html
(header>nav>ul>li.items*2>a)+(div.container>(div.sidebar+div.content))+(footer>p.muted)
<header>
  <nav>
    <ul>
      <li class="items"><a href=""></a></li>
      <li class="items"><a href=""></a></li>
    </ul>
  </nav>
</header>
<div class="container">
  <div class="sidebar"></div>
  <div class="content"></div>
</div>
<footer>
  <p class="muted"></p>
</footer>

```


### Wrapping Existing Items
1: Highlight all the text in a multi-cursor, eg (shift+left mouse and drag)
  Important: It MUST be highlighted with multi-curisors so it affects all existing items,
             otherwise it will wrap the selection only
2: Run: Emmet Wrap Abbreviations (ctrl+shift+g)
3: A box at the bottom appears (or elsewhere depending on your IDE)

```
Mon
Wed
Tue
Thu
Fri
Sat
Sun
```

In the box I entered:
```
li.day-$$>span
```

```html
<li class="dow-1">Sun</li>
<li class="dow-2">Mon</li>
<li class="dow-3">Wed</li>
<li class="dow-4">Tue</li>
<li class="dow-5">Thu</li>
<li class="dow-6">Fri</li>
<li class="dow-7">Sat</li>

```
