<script>
	
	/// Showcase on a sorting algorithm inside Svelte.
	
	/// Make sure to check out the view elements, to understand
	/// why and when a function gets called.
	
	
	/// Want to learn more? Check out my YouTube Channel "CodeBaseCamp"
	/// Happy coding!
	
	
	
	

	//Starting point. Just an Array called "numbers"
	const numbers = [];
	
	// This is used for the number that we add to the input.
	var number;
	
	
	// The Function to reorder the array. BubbleSort.
	function reOrderArray(){
		//for each Element inside our numbers array
		for(var i = 0; i<numbers.length; i++){
			
			// for each Element inisde our numbers array and i
		for(var x=0; x<numbers.length; x++){
			
			// if the number from the i loop is smaller then the number
			// from the x loop
			if(numbers[i] < numbers[x]){
				
				// save the value i quickly. 
				var num = numbers[i];
				// change the value i to the value x
				numbers[i] = numbers[x];
				// reorder the i value (stored as num here to x)
				numbers[x] = num;	
			}
			
		}
			
	 }
		
	}
	
	
	
	// Add a new number to the numbers array. 
	function test(){
		// make sure we don't push empty data to our array.
		if(number != null){
			
			// push the number (declared at the top) to the array numbers.
			numbers.push(number)
			// rerender numbers array (svelte doc's)
			numbers = numbers;
			//call the reOrderArray
			reOrderArray();
			// set the number again to null so that the field is cleared.
			// if you remove this, you will see that the number
			// in the input will be the same, even after submitting.
			number = "";
			
			
			
		} else{
			// just tell us if the data is empty.
			console.log('no number')
			// do nothing else.
			return;
		}
	}
	
	// similiar to adding an element, but instead removing it.
	function remove(num){
		
		// check if we have the id inside our array
		for(var z=0; z<numbers.length; z++){
			
			// if we have an element that is equal to the num from the list
			if(numbers[z] === num){
				// remove it via splice
				numbers.splice(z, 1)
				numbers = numbers;
			}
		}
				// rerender the array.
				

		
		
	}
	
	function addNumbers(){
		
		for(var z = 0; z<Math.floor(Math.random() * 99); z++){
			
			var random = Math.floor(Math.random() * 21321)
			
			numbers.push(random)
			numbers = numbers;
			reOrderArray();
			
			console.log(random)
		}
		
	
	}
	
	
		// Debugging
		console.log({numbers});

</script>

<h1>
	Hello fellow coder!
</h1>
<h2>
	Want to find out if 2 is greater than 1 quickly?
</h2>
<p>
	This is an easy bubble sort, done with svelte in less then 2 minutes (adding the input and figuring out the Svelte API took maybe 10 minutes). 
</p>

<h3>
	Add a Number and let Svelte do the rest for you:
</h3>
<input type="number" placeholder="Number" bind:value={number}>
<button on:click={test} on:keys.enter="{test()}">
	Add Number
</button>

<button on:click={addNumbers}>
	Add multiple Numbers at once.
</button>



<ul>
	{#each numbers as num}
	<li>
		{num} <button on:click={() => remove(num)}>
		Remove
		</button>  
</li> 
{/each}
</ul>


