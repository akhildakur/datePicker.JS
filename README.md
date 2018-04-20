# datePicker.js
This is front end javascript library which gives a GUI calendar. Best thing about this calendar is that it is complete customisable.


# What is datePicker.js ?
This is a Front End Javascript miniature calendar for choosing dates into input fields. In simple terms, if you want user     to enter a calendar date into an input form element. Instead of typing date manually, with this library you can have graphically displayed calender where user can simply click on date he wanted and it automatically gets into that input field. So, no typing !

# What features does datePicker.js has ?
  1. Complete access to all UI elements of calender with ease.
  2. Configure calendar's CSS as per your requirement (taste).
  3. Simplified calendar configuration using JSON.

# How to use ?
Follow these steps
1. Link datePicker.js source file to your HTML file, using script tags in head element.\
`<script type="text/javascript" src="PATH TO datePicker.js FILE"></script>`
2. Create an input element in the body of HTML file and give it an id.\
`<input id="xyz" type="text" placeholder="Select a Date" name="date">`
3. Now in your js file, which should link to current HTML file.In it, type the following
```javascript
//Configuration Documentation is available in the next section
//Note: Every property holds default values, which can be changed if you wish to. If you don't want to change, you can omit
//that option from typing it.
var conf = {
  el:"#xyz",
  dp:{
    model:"",
    dateFormat:"dd/mm/yyyy",
    style:"",
    outType:"insert-value",
    head:{
      style:"",
      navBtns:{
        leftBtnSymbol:"",
        rightBtnSymbol:"",
        style:"",
        styleOnHover:""
      },
      styleMonthName:"",
      styleYear:""
    },
    body:{
      style:"",
      dateStyle:{
        styleWeekNames:"",
        styleToday:"",
        styleRest:"",
        styleRestOnHover:""
      }
    }
  },
  wrapper:{
    style:"",
    tag:""
  }
};
var x = new datePickerDotJS(conf);
```
4. Open your HTML file in any browser. Now click on the input element you created if you have implemented all previous steps correctly now you will see a calendar popped out below that input element.
5. Now click on any date or go to next or previous month or year. It will appear in the input element in _dd/mm/yyyy_ format (as it was given as preferred output format in conf).

# Configuration Documentation
Configuration object is divided into three parts.They are element(el), datePicker(dp) and wrapper.
Note: Every property holds default values, which can be changed if you wish to. If you don't want to change you can omit that option from typing it.
## Element (el)
This hold the id of the element that you want to use datePicker on. It is of string type.
Example: 
```javascript
var conf = {
el:"#qwe"
}
```
The pound is kept in front because it is an id. So, if you want to use class then you go with _.CLASS NAME_ but it is not recommended because it selects only first element in the class, if there are more than one elements sharing the same class and it results in unexpected outputs.
## Date Picker (dp)
This holds both head and body of the calendar UI along with their inner element's styles and some innerHTML values. It also holds style of calendar block, the date format that we wanted as output and output type is where we want the result to store. Below you can find all these options in detail.
### Model (model)
This is type calendar you wanted to use, but currently only one type is available and it is _regular_. The default value for this option is regular and code snippet as follows
```javascript
//Default Value is regular
var conf = {
  el:"#xyz",
  dp:{
    model:"regular"
  }
};
```
You can leave this option empty or omit it for now because it has only one value and that is its default.
### Date Format (dateFormat)
This option is used to set the output date format that you want. The default value is _dd/mm/yyyy_. You can any format with 2 digit years and can even keep any special character in between like _'/,- etc.'_. You can even change positions of date, month and year. This value is of string type and this is how you change it
```javascript
// Default value is dd/mm/yyyy
var conf = {
  el:"#xyz",
  dp:{
   dateFormat:"mm-dd-yy"
  }
};
```
### Style (style)
This is the CSS style property of the calendar block. By default, it is used to show or hide calendar block. These are default css properties it holds
```css
/* Default CSS Properties*/
position:absolute;
width:400px;
height:350px;
z-index:3;
display:block;
box-shadow:0px 1px 7px #666;
```
All the above properties can be changed it you want to or if you want to add some additional styles, you can even do that. Check out examples below
#### Changing existing properties
```javascript
var conf = {
  el:"#xyz",
  dp:{
    style:"height:550px;width:500px;"
  }
};
var x = new datePickerDotJS(conf);
```
Now the height and width are changed to 550px and 500px respectively.
#### Adding new css properties
```javascript
var conf = {
  el:"#xyz",
  dp:{
    style:"background-color:white;"
  }
};
var x = new datePickerDotJS(conf);
```
Now background-color property is added to calendar block styles.
### Out Type (outType)
This options tells where you want the final output be placed at. It has two values _insert-value_ and _return-value_.. It value is of string type and default value is _inser-value_. Check out how they work below
#### Insert Value (insert-value)
This option gets the final date string like ("12/3/2018") and puts it into input element's value that was used in el option. Here is an example
```javascript
// Default value is insert-value
var conf = {
  el:"#xyz",
  dp:{
    outType:"insert-value"
  }
};
```
#### Return Value (return-value)
This option gets the final date string like ("12/3/2018") and puts it into the variable that is used when instantiating datePickerDotJS with property name _selectedDate_. Here is an example
```javascript
// Default value is insert-value
var conf = {
  el:"#xyz",
  dp:{
    outType:"return-value"
  }
};
var sd = new datePickerDotJS(conf);
```
Now after you have selected any date on UI then you can access it using __sd.selectedDate_ in JS.
## Head
This refers to the top part of the calendar, which holds navigation buttons, month name and year. It has style, navBtns, styleMonthName and styleYear. All these are explained below
#### Style (style)
This holds CSS properties for head section of the calendar. It has some default CSS properties and you can overwrite default CSS properties and add new CSS properties. It is of string type. Default CSS properties are below
```css
/* Default CSS Properties*/
height:20%;
width:100%;
background-color:white;
display:grid;
grid-template-columns:15% 45% 15% 15%;
justify-content:center;
align-content:center;
```
#### Nav Buttons (navBtns)
This holds CSS properties of navigation button, what symbol you want to use in navigation buttons and what CSS properties need to change upon hovering on navigation buttons. This is of object type. Options are explained below.
##### Left Button Symbol (leftBtnSymbol)
This holds the symbol you wanted to show as left symbol. It actually changes innerHTML of that element. So, if you are using any icons you can directly put them in here. It is of string type.Default value is _<_.
##### Right Button Symbol (rightBtnSymbol)
This holds the symbol you wanted to show as right symbol. It actually changes innerHTML of that element. So, if you are using any icons you can directly put them in here as string. It is of string type.Default value is _>_.
##### Style (style)
This holds the CSS properties of navigation buttons. It is of string type. It has some default CSS properties. You can overwrite default properties and add new CSS properties. Below are the default values
```css
/* Default CSS Properties*/
text-align:center;
padding:0px 10px;
border-radius:3px;
font-size:2.2em;
cursor:default;
```
##### Style On Hover (styleOnHover)
This holds the CSS properties of navigation buttons when hovered on them. It is of string type. It has some default CSS properties. You can overwrite default properties and add new CSS properties. Below are the default values
```css
/* Default CSS Properties*/
background-color:#d8eaf8;
color:#3580eb;
```
#### Style Month Name (styleMonthName)
This holds the CSS properties of Month Name element in head of calendar. It is of string type. It has some default CSS properties. You can overwrite default properties and add new CSS properties. Below are the default values
```css
/* Default CSS Properties*/
font-size:1.4em;
text-align:center;
align-self:center;
cursor:default;
```
#### Style Year (styleYear)
This holds the CSS properties of Year element in head of calendar. It is of string type. It has some default CSS properties. You can overwrite default properties and add new CSS properties. Below are the default values
```css
/* Default CSS Properties*/
ont-size:1.6em;
text-align:center;
align-self:center;
cursor:default;
```


## Body
This refers to the bottom part of the calendar, which holds week day names and days of a month. It has style and dateStyle.  These are explained below
#### Style (style)
This holds CSS properties for body section of the calendar. It has some default CSS properties and you can overwrite default CSS properties and add new CSS properties. It is of string type. Default CSS properties are below
```css
/* Default CSS Properties*/
height:80%;
width:100%;
background-color:#f9f9f9;
display:grid;
grid-template-columns:auto auto auto auto auto auto auto;
grid-template-rows:14% 14% 14% 14% 14% 14% 14%;
```
#### Date Style (dateStyle)
This holds CSS properties of date buttons, CSS properties of week day names, CSS properties of today date button and what CSS properties need to change upon hovering on date buttons. This is of object type. Options are explained below.
##### Style Week Names (styleWeekNames)
This holds CSS properties for week names elements of the calendar. It has some default CSS properties and you can overwrite default CSS properties and add new CSS properties. It is of string type. Default CSS properties are below
```css
/* Default CSS Properties*/
text-align:center;
padding:5px;
align-self:center;
cursor:default;
```
##### Style Today (styleToday)
This holds CSS properties for today date element of the calendar. It has some default CSS properties and you can overwrite default CSS properties and add new CSS properties. It is of string type. Default CSS properties are below
```css
/* Default CSS Properties*/
text-align:center;
padding:5px;
background-color:#3580eb;
color:#d8eaf8;
align-self:center;
cursor:default;
border-radius:4px;
```
##### Style Rest (styleRest)
This holds CSS properties for rest of dates element except today date element of the calendar. It has some default CSS properties and you can overwrite default CSS properties and add new CSS properties. It is of string type. Default CSS properties are below
```css
/* Default CSS Properties*/
text-align:center;
padding:5px;
background-color:transparent;
color:black;
align-self:center;
cursor:default;
border-radius:4px;
```
##### Style Rest On Hover (styleRestOnHover)
This holds the CSS properties of rest of the dates elements except today date element when hovered. It is of string type. It has some default CSS properties. You can overwrite default properties and add new CSS properties. Below are the default values
```css
/* Default CSS Properties*/
background-color:#d8eaf8;
color:#3580eb;
```
#### Style Month Name (styleMonthName)
This holds the CSS properties of Month Name element in head of calendar. It is of string type. It has some default CSS properties. You can overwrite default properties and add new CSS properties. Below are the default values
```css
/* Default CSS Properties*/
font-size:1.4em;
text-align:center;
align-self:center;
cursor:default;
```
## Wrapper (wrapper)
Wrapper element is the one that places _el_ element as a child inside it. It is of object type. It has style and tag name properties inside it.
```javascript
`<div class="dp-wrapper">// This is the wrapper
  <input id ="xyz" name="date"> // This is actual element that passed in with "el" property
</div>`
```
### Style (style)
This holds the CSS properties of wrapper element. It is of string type. It has some default CSS properties. You can overwrite default properties and add new CSS properties. Below are the default values
```css
/* Default CSS Properties*/
position:relative;
display:inline-block;
```
### Tag (tag)
This holds the tag name of wrapper element. It is of string type. It has _SPAN_ default value. You can overwrite this default value with any tag name that suits the purpose.




