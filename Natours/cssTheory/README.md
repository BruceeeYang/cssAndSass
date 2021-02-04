# CSS theory

#### Resolve conflict

IMPORTANT -> SPECIFICITY -> SOURCE ORDER

- IMPORTANT

```
    1. User !important declarations
    2. Author !important declarations
    3. Author declarations
    4. User declarations
    5. Default browser declarations
```

- SPECIFICITY

```
    1. inline style
    2. IDs
    3. Classes, pseudo-classes, attribute
    4. Elements, pseudo-elements
```

- SOURCE ORDER

```
    the last declaration in the code will override all other declarations and will be applied
```

##### Resolve conflict Summary

- CSS declarations make with <mark>!important</mark> have the highest priority
- Only use important as a last resource - more maintainable code
- Inline styles will always have priority over styles in external stylesheet

#### CSS engine converts relative units to pixels

```
html,body{
  font-size: 16px;
  width: 80vw;
}

header{
  font-size: 150%;
  padding: 2em;
  margin-bottom: 10rem;
  height: 90vh;
  width: 1000px;
}

.header-child{
  font-size: 3rem;
  padding: 10%;
}
```

<table>
    <tr>
        <td colspan="2"></td>
        <td>Example</td>
        <td>How to convert to pixels</td>
        <td>Result in pixels</td>
    </tr>
    <tr>
        <td colspan="2">%(fonts)</td>
        <td>150% -></td>
        <td>x% * parent's computed font-size -></td>
        <td>24px</td>
    </tr>
    <tr>
        <td colspan="2">%(length)</td>
        <td>10%</td>
        <td>x% * parent's computed <mark>width</mark> -></td>
        <td>100px</td>
    </tr>
    <tr>
        <td rowspan="3">Font-based</td>
        <td>em(font)</td>
        <td>3em</td>
        <td>x * parent computed font-size</td>
        <td>72px (3*24)</td>
    </tr>
    <tr>
        <td>em(length)</td>
        <td>2em</td>
        <td>x * current element computed font-size</td>
        <td>48px (2*24)</td>
    </tr>
    <tr>
        <td>rem</td>
        <td>10rem</td>
        <td>x * root computed font-size</td>
        <td>160px</td>
    </tr>
    <tr>
        <td rowspan="2">Viewport-based</td>
        <td>vh</td>
        <td>90vh</td>
        <td>x * 1% of viewport height</td>
        <td>90% of the current viewport height</td>
    </tr>
    <tr>
        <td>vw</td>
        <td>80vw</td>
        <td>x * 1% of viewport width</td>
        <td>80% of the current viewport width</td>
    </tr>
<table>
※ length : like height, a padding, a margin... <br>
※ em : use the <mark>parent</mark>(for fonts) or the current element(for length) as a reference <br>
※ rem : use the <mark>root</mark> font-size as the reference <br>

#### inherit in CSS

```
.parent{
    font-size: 20px;
    line-height: 150%
}

.child{
    font-size: 25px;
}
```

※ Every CSS property must have a value

In this case, that's 150% of 20px, which is 30px.
SO the line-height, the child element, will also 30px, not 150% of the 25px font-size

- Inherited: font-size, font-family, color etc.
- Not inherited: padding, margin...

#### 7-1 Pattern

###### BEM

- .block{}
  > 區塊 (Block)
- .block\_\_element{}
  > 元素 (Element)
- .block--modifier{}
  > 修飾符（Modifier）

ref:[BEM 鐵人](https://ithelp.ithome.com.tw/articles/10160545)
ref:[BEM 官方](http://getbem.com/)

###### The 7 folders

- base/
  > we are put the basic product definitions.
- components/
  > we have one file for each component.
- layout/
  > we define the overall layout of the project.
- pages/
  > we have style for specific pages of the project.
- themes/
  > if you want to implement different visual themes.
- abstracts/
  > we put code that doesn't output any CSS. ex: variables、min-ins
- vendors/
  > all third party CSS goes
