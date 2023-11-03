# HTMLBuilder 

Javascript code to create standard HTML from javascript objects.
The file htmlbuilder.html contains:
* htmlbuilder function and constants used by it
* demonstration code that uses htmlbuilder  

Open this file in a browser to see results.  

### Features  
* uses js objects to create html
* makes it easy to incorporate variables
* shortcuts to minimize coding
* simplifies generating html with javascript  

An array of objects is passed to the HtmlBuilder function. The first key of each object identifies the tag to be used. The value of the first key varies depending on the type of tag. Remaining key:value entries define attributes for the tag. These attributes can be for both html (ex: class, value) or css (ex:margin, color).    
### Example Inputs 
```
1 - {div:"#div1", b:"1px solid green", p:"5px"}
2 - {h2:"Section Heading", clr:sectionHeadingColor}
3 - {img:"img-file-path", w:"500px", h:"300px"}

``` 
### Outputs  
```
1 - <div id="div1" style="border:1px solid green; padding:5px;">
2 - <h2 style="color:red">Section Heading</h2>
3 - <img src="img-file-path" style="width:500px;height:300px;">
```

## Rules

Inputs with typeof "string" are copied asis to output.  

First key in obj must be a valid html tag.  
Tags are categorized as: text, no text, or special.
Depending on category, value of 1st key:value varies.
* text tags (h1, p, label, li, etc.)- text value of html element
* no text tags (div, select, table, ul, etc.)
    * null - nothing added
    * "#x1" - adds id="x1"
    * ".x1" - adds class="x1"
    * "*x1" - adds name="x1"
* special tags ("img", "radio", "checkbox", "inptext", "tr", "end")
    * img - value of src attribute
    * radio - same rules as noText, ex output: < input type="radio" name="rad_color"> 
    * checkbox - same rules as noText, ex output: < input type="checkbox" id="cbx_one" >
    * inptext - same rules as noText, ex output: < input type="text" id="inp1" >
    * tr - adds data-id=value attribute (typically db record id)
    * end - outputs end tag, ex: {end:"div} outputs "</ div>"

*End tags are added automatically by default, unless tag is included in the noEndTag array*

**NOTE** - Not all html tags or css styles are defined in htmlbuilder. Add as needed.
