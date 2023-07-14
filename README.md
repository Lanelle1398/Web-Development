# Web-Development
```
<!DOCTYPE html>
<html>
<body>

<h1>Higher Lower</h1>
<h2 id ="abc"> Step 1: Selecting Max</h2>

<p id="efg"> Click the button to set a maximum number.</p>

<h3 id= "xyz" ></h3> 
<p id="demo"></p>
<p id="guessed"></p>

<p id="newElementId"></p>
<p id="labelId"> </p>
<button id= "hij" onclick="myFunction()">Set it</button>




<script>
function myFunction() {

  var myBool = true;
  while(myBool) {
  //var y;
  var x = Math.round(parseFloat(prompt("Enter a maximum value", "3"))); //prompt to ask for maximum number
  if (x!=0 && x>0  && !(isNaN(x))) break; //stop prompting the user if they entered a valid max
  }

  if (x!=0 && x>0  && !(isNaN(x))) { //only takes valid entries to set as max: non negative, not zero and only numbers
    document.getElementById("abc").innerHTML =
    ""; //remove Step 1: Selecting Max
    document.getElementById("efg").innerHTML =
    ""; //remove "click the button to set a max number" label
   
    document.getElementById("xyz").innerHTML =
    "Step 2"; //add step 2 label
    document.getElementById("demo").innerHTML =
    "Now guess a number between 0 and " + x; //add new label "now guess a number between 0 and max"
    document.getElementById("guessed").innerHTML =
    "Your guess:"; //add your guess label
  
     // create a new textbox for step 2
    var txtNewInputBox = document.createElement('div');
    txtNewInputBox.innerHTML = "<input type='text' id='newInputBox'>";
    document.getElementById("newElementId").appendChild(txtNewInputBox);
    document.getElementById("hij").style.visibility="hidden"; //hide the set max N button

    //create a new button for step 2
    var btn = document.createElement("button");
    btn.innerHTML = "Guess";

    var array = []; // create an empty array to keep track of the guesses
    var num = Math.floor(Math.random() * x) + 1; //choose a random number between 0 and the maximum number
    btn.onclick = function () {
      //guessing game

        mess2 = Math.floor(document.getElementById("newInputBox").value);  //this is the number the user guessed
       // console.log(num);
       
        //before pushing to the array , check to make sure that the number has not already been guessed
        if(mess2 == num && !(mess2 > x || (mess2 <1)) || mess2 > num && !(mess2 > x || (mess2 <1)) || mess2 < num && !(mess2 > x || (mess2 <1))){
                   
          if (!array.includes(mess2)) { //check to see if the array does not already have the number
          // only runs if value not in array
            array.push(mess2);
            var YES = true;
          } 

          else{
            document.getElementById("labelId").innerHTML="The number has already been guessed"; //if the number has already been guessed, don't bother saying higer, lower, etc, var yes is not true
          }
        
          var z=array.length;
            if(YES){
               //only valid numbers go through these loops and are added to the array
              if(mess2 == num && !(mess2 > x || (mess2 <1))) {   
                document.getElementById("labelId").innerHTML ="You got it! It took you " + array.length + " try/ tries and your guesses were " + array + ".";
              }
              if (mess2 > num && !(mess2 > x || (mess2 <1))) {
                  document.getElementById("labelId").innerHTML = "No try a lower number";
              }
              if (mess2 < num && !(mess2 > x || (mess2 <1))) {
                document.getElementById("labelId").innerHTML = "No try a higher number";
              }
            }
         
        }
        //invalid numbers go through these loops ///
        if (mess2 > x || (mess2 <1) ) {
            document.getElementById("labelId").innerHTML = "That number is not in range, try again.";
        }
        if ((isNaN(mess2))) {
          document.getElementById("labelId").innerHTML = "That is not a number!";
        }
    };
    document.body.appendChild(btn);
  }

  else{ //non negative, 0s and things that are not numbers are invalid for the max
    alert('invalid entry; please re set');
  }
}
</script>



</body>
</html>

```
