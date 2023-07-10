# Vue.JS

AuthGuard: (written by CW)
Can add it to any route ‘beforeEnter: authGuard’
Makes sure that the user is authorized to enter the page 
Do you have a valid bearer token? If not then you are logged in with a redirect and then bring you back to the original page 

AuthSettled: (written by CW)
Says that you are allowed to go to this page or on this route, but there is a delay before loading because its checking that the auth system has fully loaded 
Makes sure that the auth system is done running its checks before it loads to the page 
Can access pages if you are not logged in 

BCW TEMPLATE:
To flip the view → change the flex direction to row in main.scss (this will change the direction of everything else)

Computed: computed properties can be used to calculate and display values based on a value or set of values in the data model 
Can also attach logic 

onMounted: registers a callback to be called after the component has been mounted
Lifecycle hook 



watchEffect: reactive dependency watching
Takes in two parameters, the function and the object options 
Code that is placed inside of the function will trigger immediately as JS reaches this line of code 

Ref:
Const editable = ref({})
Editable is the thing that is bound in the form, that is going to be edited
Will reference the object we will edit/create 
Return the editable to make is accessible to the form, the form will send the editable.value to the service (.value will be all the values that are in the form)
***Can use a ternary for the editable for the handle submit function between the editFunction and createFunction 
V-model: will go into the object (the editable) and take whatever the property is (that is found in the model) and it's going to keep that property on the object up to date whenever we type it into the form 
It's going to bind the model property to the object we are creating or editing 
Can return an array of strings under the return that are accessible in the form with a v-for and binding the value (good when you want to use an option tag)


Props: custom attributes you can register on a component 
When a value is passed to a prop attribute its becomes a property on that component instance 
The value becomes accessible within the template and on the components ‘this’ context 
A component can have as many props as you like 
Will need to v-for over the component we wanted rendered 
Ex. v-for=”post in posts”

Slots: vue slot component ***LOOK AT THE DOCS
Ids on the slots need to be specific 
<Modal id=”slotOne”>Text will go here</Modal>
<Modal id=”slotTwo”>Text will go here</Modal>
Can passed props in a form such as modalTitle so that the title of the modal changes 
Use ‘<template #slotName></template>’ to target a named slot with the same name in a component or page 

RouterLink:
When router links are added we have to specify the ‘to’ property (they will break the page and prevent it from loading if you don’t include the to property)
The ‘to’ property uses named routing which means it needs to be bound == ‘:to=”{name: ‘Home’}’
Named routing in Vue is case-sensitive 
Adding parameters will also break your entire page if they are not correct 
Be mindful of forward slashes BUT in named routing, names take care of the pathing for the developer 

RouterPush: 