# MIPS

Asks the user to input an integer between the values 10 and 20, the value is stored, and another prompt for 
another integer is asked that needs to be greater than -15. The two integers are taken and computed in the equation: 
16*int1+ 9*(int2 -7). A result message with the result value is printed. The program will repeat
until entering the value -20 which will exit the program. 

#PSUEDO CODE

println("Enter an integer between 10 and 20, [-20 EXIT]: ");		//repeat for integer2, where < -15
int val1;								//initialize variables
int val2;
while(val1 < 10 || val1 > 20){
	println("Error: Value exceeds parameters"); }
while(val2 < -15){
	//print the same error message
if(val1== -20 || val2== -20){
	exit; }
