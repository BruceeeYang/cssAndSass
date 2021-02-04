# SASS and NPM

### SASS

ref: [codepen example](https://codepen.io/bruceeeyang/pen/GRNRJpR?editors=1100)

##### feature

- Variables
  > for reusable value such as color, font-size, spacing, etc;
- Nesting
  > to nest selectors inside of one another,allowing us to write less code;
- Operator
  > for mathematical operator right inside of CSS;
- Partials and imports
  > to write CSS in different files and importing them all into one single file;
- Mixins
  > to write reusable pieces of CSS code;
- Functions
  > similar to mixins, with the difference that they produce a value that can than be used;
- Extends
  > to make different selectors inherit declarations that are common to all of them;
- Control directives
  > for writing complex code using conditionals and loop

##### Install SASS

### SASS variables and nesting

#### variables

> can store data, reuse the data all over our code

define a variable name starting with dollar sign $ <br>

```
$color-primary: #f9ed69

nav{
  background-color: $color-primary
}
```

#### nesting

CSS<br>

```
.navigation {
  list-style: none;
}
.navigation li {
  display: inline-block;
  margin-left: 30px;
}
.navigation li:first-child {
  margin: 0;
}
.navigation li a {
  text-decoration: none;
  text-transform: uppercase;
}
```

SCSS<br>

```
.navigation{
  list-style:none;

  li{
    display:inline-block;
    margin-left: 30px;

    &:first-child{
    margin:0;
    }

    a{
      text-decoration:none;
      text-transform:uppercase;
    }
  }
}
```

##### CSS float

```
<nav class="clearfix">
  <div class="navigation">...</div>
  <div class="buttons">...</div>
</nav>

```

```
.clearfix::after{
  content:"";
  clear:both;   // clear this float
  display: table
}

.navigation{
  float:left
}

.buttons{
  float: right
}
```

### mixin

> a reusable piece of code, we write into a mixin

```
@mixin clearfix{        //setting a variable called clearfix
  &::after{
    content:"";
    clear:both;
    display: table;
  }
}

nav {
  margin:30px;
  background-color: #color-primary;

  @include clearfix        // using the name of the mixin.
}


```

##### change the mixin property value

```
@mixin style-link-text($color){
  text-decoration: none;
  text-transform: uppercase;
  color: $color
}

.btn-main:link,
.btn-hot:link{
  ...
  @include style-link-text($color-text-light)
}

.navigation{
  li{
    a:link{
      @include style-link-text($color-text-dark)
    }
  }
}
```

### function

```
@function divide($a, $b){    //setting a function call divide
  @return $a / $b
}

nav{
  margin: divide(60, 2)*1px;
  //using divide function and setting unit
}
```

### extend

##### NO extend

```
.btn-main:link,
.btn-hot:link{
  padding:10px;
  display:inline-block;
  text-align:center;
  border-radius:100px;
  width:$width-button;
  @include style-link-text($color-text-light);
}

.btn-main{
  &:link{
    background: $color-secondary;
  }
  &:hover{
    background: darken($color-secondary, 15%)
  }
}

.btn-hot{
  &:link{
    background: $color-tertiary;
  }
  &:hover{
    background: lighten($color-tertiary, 15%)
  }
}
```

##### extend

```
%btn-placeholder{
  padding:10px;
  display:inline-block;
  text-align:center;
  border-radius:100px;
  width:$width-button;
  @include style-link-text($color-text-light);
}

.btn-main{
  &:link{
    @extend %btn-placeholder;
    background: $color-secondary;
  }
  &:hover{
    background: darken($color-secondary, 15%)
  }
}

.btn-hot{
  &:link{
    @extend %btn-placeholder;
    background: $color-tertiary;
  }
  &:hover{
    background: lighten($color-tertiary, 15%)
  }
}
```

#### command line

###### dir

> To see the contents of that folder

###### cd

> To move inside of one of these folders

```
cd 資料夾名稱
```

> Go back to last folder

```
cd..
```

###### tab

> auto complete the name

###### cls

> clear cmd's data

###### mkdir

> create a new folder

```
mkdir 資料夾名稱
```

###### echo

> create a new file

```
echo >"檔案名稱.副檔"
```
