# GoodUI
[![codecov](https://codecov.io/gh/leonid-io/dc-ui/branch/master/graph/badge.svg)](https://codecov.io/gh/leonid-io/dc-ui)


Conquer complex UIs with GoodUI. 

## Benefits
- Rapidly build complex UIs.
- Massive reduction in Cognitive Load
- Cleaner(ish) Markup
- Build a deisgn vocabulary
- Faster front end Development
- Rapid UI iterations


## Installation

Add this line to your application's Gemfile:

```ruby
gem 'good_ui'
```

Copy the initializer and the default markup elements.

```bash
rake good_ui:setup
```

This copies the initializer and a markup configuration file **markup.yml**

## What it looks like

Presented in slim for extra sexiness ..

```slim

= container
  = grid
    = column computer: 8, tablet: 10, mobile: 16
      = segment class: 'green'
        p first paragraph
    = column size: 16, only: :computer
      = segment class: 'secondary'
        = header tag: :h1, class: 'dividing', text: 'Big Header'
        p second paragraph
```

## How it works

The ui.yml file contains a list of ui elements such as **container** and **grid**. 
It defines **default html tag** and **default css classes**.

```yaml
container:
  tag: div
  css_class: 'container'
grid:
  tag: div
  css_class: 'grid'
```

You can have multiple css classes assigned to a single element

```yaml
column:
  tag: div
  css_class: 'wide column'
```

The elements can be accessed in views by calling them as a function name

```slim
= grid
```

This produces 

```html
<div class="ui grid"></div>
```

Notice that **ui** class is automatically added. This behavior can be disabled by 
setting **ui** property to false

```yaml
grid:
  tag: div
  css_class: 'grid'
  ui: off
```

The same functionl call 

```slim
= grid
```

will now produce

```html
<div class="grid"></div>
```

### Options

You can specify column size

```slim
= column size: 8
```

This will produce

```html
<div class="eight wide column"></div>
```

You can specify different sizes for **computer**, **tablet** and **mobile**.

```slim
= column computer: 8, tablet: 6, mobile: 16
```

Will produce

```html
<div class="eight wide computer ten wide tablet sixteen wide mobile wide column"></div>
```

You can make items only visible on **computer**, **tablet** and **mobile**.

```slim
= column only: :computer
```

Will produce

```html
<div class="computer only wide column"></div>
```

### Custom Elements
Don't forget you can add your own elements. All you have to do is customize ui.yml
```yaml
hero:
  tag: div
  css_class: 'segment hero'
  ui: off
```

calling the custom function

```slim
= hero
  h1 hello world
```

will produce

```html
<div class="segment hero"><h1>Hello World</h1></div>
```

## Contributors
- [Leonid Medovyy]()


## License
The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
