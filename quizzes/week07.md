# Advanced Front-End Frameworks


**1.** Describe the two ways to bind Data in Vue?
<!-- enter you answer in the space below -->
```
Two ways to bind data in Vue:
- 'mustache syntax' using double curly braces {{}}, insert data to get it to the page 
- 'v- directives' a directives jobs is to reactively apply special behavior to the DOM when the value of its expression changes 
```

**2.** The `SPA` acronym stands for what?
<!-- enter you answer in the space below -->
```
SPA = Single Page Application 
```
**3.** What are some of the advantages/uses of a `SPA` over a traditional one?
<!-- enter you answer in the space below -->
```
SPA sites are more efficient in terms of processing, and they demand less times from developers because they are able to use repetitive layouts 
```
**4.** What does the `onMounted` method in Vue do?
<!-- enter you answer in the space below -->
```
onMounted is a lifecycle hook that is used to send an HTTP request to fetch data that the component will render 
```
**5.** What is the `v-model` attribute in Vue for, and when might you use it?
<!-- enter you answer in the space below -->
```
The v-model attribute is used to create two-way data binding on form inputs, textarea, and select element. It will automatically pick the correct way to update the element based on the input type 
```
**6.** The `v:on` (`@`) directive can be used for what?
<!-- enter you answer in the space below -->
```
V-on is a directive that requires an argument, the value must be a function or statement. V-on will attach a listener to the element the can make updates to the page 
```
**7.** Which Vue attributes(directives) could you use to conditionally render elements on a page?
<!-- enter you answer in the space below -->
```
V-if/V-else/V-else-if/v-show directives are used to conditionally render a block 
```
**8.** What is the purpose of the `key` attribute when using `v-for` on an element?
<!-- enter you answer in the space below -->
```
using the key will give a direct reference to the index the v-for is using for the array. The key makes sure that vue.js is keeping track of the items 
```
**9.** What is the `<slot>` element and what is it used for?
<!-- enter you answer in the space below -->
```
the slot element returns the name of the shadow DOM slot the element is inserted in. It is a placeholder inside a component that users can fill with their own markup 
```