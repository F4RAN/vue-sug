
you can create your button with your suggests

**Demo:**  [http://byParsa.me/Plugins/vue-sug](http://byParsa.me/Plugins/vue-sug)

## vue-sug
### Install

    npm install vue-sug --save

## Import

### Globally : 
Import plugin in your  `main.js`  file globally.

    import vueSug from  'vue-sug';
    Vue.use(vueSug)
    /*
    
    Example:
    
    Vue.use(vueButtonIcon, { color: "white" 
	, bgColor:"red"
		...
	  })
    
    ...
    
    <vue-sug :color="'white'"></vue-sug>
    
    */
### Locally : 
Import plugin in your `component` directly.

    import { vueSuggestion } from  'vue-sug'
    
    export  default {
    
	    components:{
		    vueSuggestion
		}
    }
    <vue-suggestion :color="'white'"></vue-suggestion>

## Props:

|Name|Type|Default|Description|
|--|--|--|--|
| `suggests` | String | *inExample | `color` define input text and icon color|
| `color` | String | gray | `color` define input text and icon color|
|`bgColor`|String | transparent |`bgColor` property allows you change the background color if you want|
|`startAt`|Number|3|`startAt` property shows after how many charecters suggestions start 
|`placeHolder`|String|Enter what you want|`placeHolder` property allows you change the input placeholder
`iconClass`|String|fa fa-search| `icon` property allows you to use the fontawesome icons with class name , you can use custom classes too 


## EventEmmiters

@click > at icon click
@itemClick > at suggests click



## Example:
	<template>
		<div>
			<vue-suggestion 
			:color="'white'"
			:suggests="suggestions"
			@input="string = $event.target.value"
			@click="search()"
			@itemClick="select($event)"
			></vue-suggestion>
		</div>
	</template>
	<script>
	export  default {
		data(){
			return{
			suggests:[
				{
				option:'FirstItem',

				description : 'description 1',

				status:'status1',

				} , {

				option:'SecondItem',

				description : 'description 2',

				status:'status2',

				} , {

				option:'ThirdItem',

				description : 'description 2',

				status:'status3',

				}
							]
							}
						}
					}
	
	methods:{
		search(){
		//this method triggered when you click on icon
		}
		item(e){
		//this method triggered when you click on a suggest
		}
	}
	</script>"# vue-sug" 
