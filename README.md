# PolymerExtend

This is a simple library which enables you to do OOP with Polymer 1.0+ definitions objects. 

The concept of PolymerExtend is not to do much work so the only task polymer extend does is to merge the objects in the inheritance chain. It also stores these class files under a namespace in PolymerExtend for easy access.

PolymerExtend calls the Polymer() function internally so you dont need to worry about that.

##Installation 

Simply grab the library from github or bower and point to the PolymerExtend.js in your HTML page.

##Usage

PolymerExtend() is the same as Polymer() with two new parameters

``` 
PolymerExtend(className:String, extends: String|Array, definition: Object)
``` 

`className` : This is mandatory and is the name of the class  
`extends`: This is optional but you specify the classes or class you wish to inherit either as String value or multiple String values for multiple inheritance.
`definition`: this is the polymer definition you place in `Polymer()`

##Example
```html
<script>
PolymerExtend('BaseElement',{
		getMessage:function () {
			console.log('message from parent');
		},
		getOther: function (){
			this.textContent += ' and this message is from the base class';
		}
	});

	PolymerExtend('MyElement',['BaseElement'],{
		is:'my-element',
		ready:function () {
			console.log('ready');
			this.getMessage();
			this.getOther();
		},
		getMessage: function () {
			console.log('message from child');
			this.textContent = 'This is inherited from BaseElement';
		}
	});
	</script>
<my-element></my-element>
```

##How to not create a tag

If you wish to create classes wish you dont want to create html tags for just remove the `is` attribute from the definition.

