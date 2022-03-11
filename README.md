# cs061-lab
lab 9 for CS 061 class
.orig x3000
;this stack lab computes the polish notation of a set of calls
;push_val(4) pushes the value 4 onto the stack [4]
LD R1, four
LD R5, stack
LD R6, push_val
JSRR R6



;push_val(3) pushes the value 3 onto the stack [4,3]
ADD R1, R1, #-1
LD R6, push_val
JSRR R6

;push_val(2) pushes the value 2 onto the stack [4,3,2]
ADD R1, R1, #-1
LD R6, push_val
JSRR R6



;add_val() pop 3,2 and push the result of 3+2 onto the stack [4,5]
ADD R5, R5 #1
LD R6, add_val
JSRR R6

;add_val() pop 4,5 and push the result of 4+5 onto the stack[9]
LD R6, add_val
JSRR R6

ADD R4, R1 #0

;move the top value of the stack into r4
HALT 
push_val    .Fill x3400
add_val     .FILL x3800
stack       .FILL x4000
four        .FILL #4
.end





.orig x3400 ;;push_val(int val)implement your push function that will push a value onto the stack
ST R7, backupR7 

STR R1, R5 #0
ADD R5, R5, #-1

LD R7, backupR7
RET
backupR7 .BLKW #1 
.end

.orig x3800 ;; add_val() pops two values from the top of the stack and pushes the result of adding the poppped value into the stack
ST R7, backup_R7

;R1 is 2 and R2 is 3
LDR R1, R5 #0
ADD R5, R5 #1
LDR R2, R5 #0

;3+2
ADD R1, R1, R2
STR R1, R5 #0

LD R7, backup_R7
RET
backup_R7 .BLKW #1 

.end



.orig x4200 ;;data you might need

.end
