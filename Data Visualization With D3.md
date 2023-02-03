### D3 or D3.js
- Data Driven Documents
- JavaScript Library 
- used to create dynamic and interactive data visulizaitons in the browser
- built to work with common web standards - HTML, CSS, SVG (scalable vector graphics)
- supports many different kinds of input data formats.

### ADD DOCUMENT ELEMENTS WITH D3
- several methods to let add & change elements in the document.
- the <strong>select()</strong> method selects one element from the document.
- takes an argument for the name of the element you want
- returns an HTML node for the first element in the document that matches the name. 
- Eg.
```
const anchor = d3.select("a");
```
- <strong>Append()</strong> method takes an argument for the element you want to add to the document
- It appends an HTML node to a selected item, and returns a handle to that node.

- <strong>Text()</strong>  method either sets the text of the selected node, or gets the current text. 
- To set the value, you pass a string as an argument inside the parentheses of the method.

- Eg.
```
d3.select("body")
      .append("h1")
      .text("Learning D3")
```
- The d3 part of the example is a reference to the D3 object, which is how you access D3 methods
- D3 allows you to chain several methods together with periods to perform a number of actions in a row.


### SELECT A GROUP OF ELEMENTS WITH D3
- D3 also has the selectAll() method to select a group of elements. 
- returns an array of HTML nodes for all the items in the document that match the input string.
- Like the select() method, selectAll() supports method chaining, and you can use it with other methods.

### WORK WITH DATA IN D3
- The D3 library focuses on a data-driven approach.
- When you have a set of data, you can apply D3 methods to display it on the page.
- Data comes in many formats, but this challenge uses a simple array of numbers.
- The first step is to make D3 aware of the data. 
- The data() method is used on a selection of DOM elements to attach the data to those elements. 
- The data set is passed as an argument to the method.
- A common workflow pattern is to create a new element in the document for each piece of data in the set. 
- D3 has the enter() method for this purpose.
- When enter() is combined with the data() method, it looks at the selected elements from the page and compares them to the number of data items in the set.
- If there are fewer elements than data items, it creates the missing elements.
- Eg.
```
<body>
  <ul></ul>
  <script>
    const dataset = ["a", "b", "c"];
    d3.select("ul").selectAll("li")
      .data(dataset)
      .enter()
      .append("li")
      .text("New item");
  </script>
</body>
```
- Firstly, D3 select the ul on the page.
- The all list items gets selected, which returns an empty selection.
- Then the data() method reviews the dataset and following code runs three times, once for each item in the array. 
- The enter() method sees there are no li elements on the page, but it needs 3 (one for each piece of data in dataset). 
- New li elements are appended to the ul and have the text New item.

### WORK WITH DYNAMIC DATA IN D3
- The D3 text() method can take a string or a callback function as an argument.
- Eg: if dataset = [1,2,3], append heading as 1 USD, 2 USD, 3 USD
```
.text((d)=>d + ' USD')
```
- In the example above, the parameter d refers to a single entry in the dataset that a selection is bound to

### ADDING INLINE STYLING TO ELEMENTS
- The style() method takes a comma-separated key-value pair as an argument. 
- Eg.
```
.style("font-family","verdana")
```

### CHANGE STYLE BASED ON DATA
-  you may want to color a data point blue if it has a value less than 20, and red otherwise. 
-  You can use a callback function in the style() method and include the conditional logic. 
-  The callback function uses the d parameter to represent the data point
```
selection.style("color", (d) => {

});
```
```
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];
    d3.select("body").selectAll("h2")
      .data(dataset)
      .enter()
      .append("h2")
      .text((d) => (d + " USD"))
      // Add your code below this line
      .style("color", (d) => {
        if(d < 20){
          return "red"
        }
        else{
          return "green"
        }
      })
  </script>
</body>
```

### ADD CLASSES WITH D3
- D3 has the attr() method to add any HTML attribute to an element, including a class name.
- The attr() method works the same way that style() does.
- It takes comma-separated values, and can use a callback function. 
- Here's an example to add a class of container to a selection:
```
selection.attr("class", "container");
```
- the class parameter will remain the same whenever you need to add a class and only the container parameter will change.

### UPDATE THE HEIGHT OF AN ELEMENT DYNAMICALLY
```
selection.style("cssProperty", (d) => d)
```
- EG.
```
.style('height', d => `${d}px`)
```
- style() method to the code in the editor to set the height property for each element. 
- Using a callback function to return the value of the data point with the string px added to it.

### SVG IN D3

