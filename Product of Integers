#######################################################################################################################
#REGISTER USE
#$a0 : addressing 
#$zero : zero register
#$v0, $v1 : users input values
#$t0, $t1 : input values' storage
#$s2, $s3, $s4 : constants
#$s5 : sum of computation
#######################################################################################################################
	
 
.data
	prompt1: .asciiz "\n Enter an integer between 10 and 20, [-20 EXIT] :  "
	prompt2: .asciiz "\n Enter an integer greater than -15, [-20 EXIT] :  "
	confirm1: .asciiz "\n This is your integer 1: "
	confirm2: .asciiz "\n This is your integer 2: "
	result: .asciiz "\n Using your integers, [16*int1+ 9*(int2 -7)] = : "
	invalid: .asciiz "\n Out of specified bounds. Try again: "
.space 60
.text
main:
	#initalize
	li $s2, 16
	li $s3, 9
	li $s4, 7
	
	#print the prompt for user to enter an integer
	li $v0, 4
	la $a0, prompt1
	syscall 
	
	#get the user's integer
	li $v0, 5
	syscall
	
while:
	#sentinel value
	beq $v0, -20, exit
	
	#enforcing specified ranges
	slti $s0, $v0, 10
	bne $s0, $zero, error
	
	slti $s0, $v0, 20
	beq $s0, $zero, error

	#save int1 to $t0
	move $t0, $v0
	
	#print the confirm 1 prompt 
	li $v0, 4
	la $a0, confirm1
	syscall
	
	#print the users integer 1
	li $v0, 1
	move $a0, $t0
	syscall

	#print the prompt for the integer 2
	li $v0, 4
	la $a0, prompt2
	syscall
		
	#get the users input
	li $v0, 5
	syscall

while2:
	#sentinel value
	beq $v0, -20, exit
	
	#enforcing specified range
	slti $s0, $v0, -15
	bne $s0, $zero, error2
	
	#save int2 to $t1
	move $t1, $v0
	
	#print confirm 2 prompt
	li $v0, 4
	la $a0, confirm2 
	syscall
	
	#print users integer 2 input
	li $v0, 1
	move $a0, $t1
	syscall
	
	#computing (16 * int1 + 9 * (int2 - 7))
	mul $s2, $t0, $s2	#16 * int1, quotient stored to $s2
	sub $s4, $t1, $s4	#(int2 - 7), stored to $t4
	mul $s3, $s3, $s4	#9 * (int2 - 7), stored to $t3
	add $s5, $s2, $s3	#$s2 + $t3, stored to $t5
	
	#print result prompt 
	li $v0, 4
	la $a0, result
	syscall
	
	#print result from computation
	li $v0, 1
	move $a0, $s5
	syscall
	b main
	
	#end of program
	li $v0, 10
	syscall

error:
	li $v0, 4
	la $a0, invalid
	syscall
	#get the users input
	li $v0, 5
	syscall
	b while
	
error2: 
	li $v0, 4
	la $a0, invalid
	syscall
	#get the users input
	li $v0, 5
	syscall
	b while2
	
exit:
	#end of program
	li $v0, 10
	syscall
	
