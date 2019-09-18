# Homework 

# caml seminar 

------

## exercise 3.5 

### 1

the first function takes an int as input and outputs an int. if the input is 1, the output will also be one but if the input is any other integer, it outputs 0, because of the first parameter in the case of x = 0, but due to rounding down any calculations made by the second pattern match in any other case.

### 2 

to eliminate the error, we must add a third match case, in the form of : 

```ocaml
# let switchonoff x = match x with
	| "on" -> true
	| "off" -> false
	| _ -> failwith"bad argument given, must be a boolean written as a string"
```

this program then takes any string argument and outputs boolean values if they match two values (on/off) and fails otherwise.

### 3 

```ocaml
let a = 42 and b = 666 in 
	match a * b - 27972 with 
		| 0 		   -> "zero"
		| x when x > 0 -> "positive"
		| _			   -> "negative";;
```

this one doesnt do much as it isnt a function, multiplies 42 by 666, giving us 27972, then subtracts 27972 from it, and then checks whether the value is 0, positive or negative, nothing to change here.

### 4 

I'm getting tired of writing these by now and would love them to be availabe online
you should not have the second match case and use "_" instead bc if $x \not > 0$ then $x \leq 0$.

### 5 

this one gives an error bc 34 is not in the cases define by the match
to fix it we cna do smthg like this ; 

```ocaml
let parity n = let unit = n mod 10 in match unit with 
	| 0 | 2 | 4 | 6 | 8 -> "even"  
	| 1 | 3 | 5 | 7 | 9 -> "odd"
```

### 6 

wrong order, start from A then descend, otherwise the first matching case is chosen 

### 7

```ocaml
let h x y = if x = 0 then 0 else if x = y then 1 else -1  
```

### 8



------

## exercise 3.6

### 1 

```ocaml
let test a = 
	let f n =
		if n < 0 then
			-1
		else 
			1
	in
	match f a * a with
		0 | 1 | 2 | 3 | 4 -> true 
		| n when n >= 10 -> false 
        | _ -> true 
```

this is an int --> bool function, it outputs true if a < 10, false otherwise.
this it the same as this function : 

```ocaml
let test a = 
	match a with 
	| x when x < 10 -> true
	| x when x >= 10 -> false
	| _ -> failwith"invalid argument"
```

### 2 

```ocaml
let f a b = match a with 
	| 0  -> 0 
	| x when x < 0 	-> 	(match b with
							| 0 			-> 0
							| _ 			-> -x + x/b*b
						)
	| x				-> 	(match b with
							| 0 			-> 0
							| y when y < 0 	-> x - (x/(-y))*(-y)
							| y 			-> x - x/y*y
						);;
```

this just takes the smallest of the two values and outputs it..... os its exactly like min2 that we did for yesterday : 

```ocaml
let f a b = if a < b then 
				a 
			else 
				b ;;
```

------

## exercise 3.7

### 1 

```ocaml
let rate_eco w = match w with
	| x when x < 0 		-> failwith "value is negative"
	| x when x <= 500 	-> "3.4$"
    | x when x <=1000 	-> "4.6$"
    | x when x <=2000 	-> "5.1$"
    | x when x <=3000 	-> "6.9$"
    | _ 				-> failwith "value is above 3000"
```

### 2 

```ocaml
let rate_standard w = match w with
	| x when x < 0 		-> failwith "value is negative"
	| x when x <= 500 	-> "4.6$"
    | x when x <=1000 	-> "5.9$"
    | x when x <=2000 	-> "6.5$"
    | x when x <=3000 	-> "7.2$"
    | _ 				-> failwith "value is above 3000"
```

```ocaml
let rate_express w = match w with
	| x when x < 0 		-> failwith "weight is negative"
	| x when x <= 500 	-> "9.1$"
    | x when x <=1000 	-> "11$"
    | x when x <=2000 	-> "13.5$"
    | x when x <=3000 	-> "14.2$"
    | _ 				-> failwith "weight is above 3000"
```

### 3 

```ocaml
let rate w t = match t with 
	| "eco" 		-> match w with 
						| x when x < 0 		-> failwith "value is negative"
						| x when x <= 500 	-> "3.4$"
   						| x when x <=1000 	-> "4.6$"
    					| x when x <=2000 	-> "5.1$"
    					| x when x <=3000 	-> "6.9$"
    					| _ 				-> failwith "value is above 3000"
	| "standard" 	-> match w with
						| x when x < 0 		-> failwith "value is negative"
						| x when x <= 500 	-> "4.6$"
                        | x when x <=1000 	-> "5.9$"
                        | x when x <=2000 	-> "6.5$"
                        | x when x <=3000 	-> "7.2$"
                        | _ 				-> failwith "value is above 3000"
	| "express" 	-> match w with
                        | x when x < 0 		-> failwith "weight is negative"
                        | x when x <= 500 	-> "9.1$"
                        | x when x <=1000 	-> "11$"
                        | x when x <=2000 	-> "13.5$"
                        | x when x <=3000 	-> "14.2$"
                        | _ 				-> failwith "weight is above 3000"
 	| _ 			-> failwith"type argument is eco, standard or express"              
```

------

## exercise 3.10 

### 1 

```ocaml
let roman x = 
if x <= 3999 && x > 0 then
	if x >= 1000 then 
		let thousands = x / 1000 and 
		hundreds = (x mod 1000) / 100 and 
		tens = (x mod 100) / 10 and 
		dec = x mod 10  
	else 
		let thousands = 0 
		if x >= 100 then 
			let hundreds = (x mod 1000) / 100 and 
			tens = (x mod 100) / 10 and 
			dec = x mod 10 
		else 
			let hundreds = 0 
			if x >= 10 then 
            	let tens = (x mod 100) / 10
            else 
            	let tens = 0 and 
            	dec = x in match dec with 
            	| 1 -> "I"
            	| 2 -> "II"
                | 3 -> "III"
                | 4 -> "IV"
                | 5 -> "V"
                | 6 -> "VI"
                | 7 -> "VII"
                | 8 -> "VIII"
                | 9 -> "IX"
else 
	failwith"value out of bounds"
(* I now realise the function i am writing is way too big and there has to be a more efficient way to do this yet i am confused and have no idea what to do....
It is currently 1am yet I am up trying to understand how caml syntax works and i am very confused*)
```



------



## exercise 3.8 

### 1 

first line outputs a, a tuple of type ((int * bool)*string) == ((1,true)“one”)

### 2 

$\not\Delta$ I have no idea why this works like this but it outputs c as the same values and type as a $\ldots$

### 3

this is a function of type int*bool -> int * (int*bool)

### 4

the second one fails bc f expects a tuple as input and is given a single value for x and therefore cannot do anything$\ldots$or so i think ????

### 5

this function checks how many roots a given function of type $ax^2+bx+c$, altho it gives the output no root for $\Delta < 0$, when it should give roots in imaginary numbers.
this function could be applied to a math problem with such equation in order to facilitate its solving, wltho in this case it should also output the value of $\Delta$. 

### 6

$\not\Delta$ I seriously dont get this one tho 

### 7

this one seems to output arbitrary values for the arguments given, 2 if not matching, 1 if (1,true) _ etc, seems a bit useless tbh

### 8

I’m dying help me ... 

altho what i think this does is again just check for the values and give an arbitrary output,
it may have something to do with sinuses of an x position and a y position but at this point its just guess work

### 9

turns a command with operators written as strings into the command with the integer operators 
x “and” y -> x && y
could be cool if writting a written language calculator or something of the sort 

### 10

simply checks if the second member of a tuple is the same as the first one and outputs true or false if it is or not 

### 11

does the same thing as above but is written a bit less well IMHO

------

## exercise 3.10

```ocaml
let roman x =
if x < 3999 && x > 0 then
	if x >= 1000 then 
		let str_x = string_of_int x 
	else
		if x >=100
			let str_x = "0" ^ string_of_int x 
		else 
			if x >=10 then 
				let str_x = "00" ^ string_of_int x 
			else 
				let str_x = "000" ^ string_of_int x 
	in	
	
    let tho = int_of_string(Char.escaped str_x.[0])	and
        hun = int_of_string(Char.escaped str_x.[1]) and
        ten = int_of_string(Char.escaped str_x.[2]) and
        dig = int_of_string(Char.escaped str_x.[3]) in 
		let x1 = match tho with 
			  0 -> ""
			| 1 -> "M"
			| 2 -> "MM"
			| 3 -> "MMM"
			| x when x < 10 ->
			   failwith "conv_thousands: thousand digit > 3"
			| _ -> invalid_arg "conv_thousands: not a digit"
		and x2 = match hun with 
			  0 -> ""
			| 1 -> "C"
			| 2 -> "CC"
			| 3 -> "CCC"
			| 4 -> "CD"
			| 5 -> "D"
			| 6 -> "DC"
			| 7 -> "DCC"
			| 8 -> "DCCC"
			| 9 -> "CM"
			| _ -> invalid_arg "conv_hundreds: not a digit"
		and x3 = match ten with 
			  0 -> ""
			| 1 -> "X"
			| 2 -> "XX"
			| 3 -> "XXX"
			| 4 -> "XL"
			| 5 -> "L"
			| 6 -> "LX"
			| 7 -> "LXX"
			| 8 -> "LXXX"
			| 9 -> "XC"
			|  _ -> invalid_arg "conv_tens: not a digit" 
		and x4 = match dig with 
			  0 -> ""
			| 1 -> "I"
			| 2 -> "II"
			| 3 -> "III"
			| 4 -> "IV"
			| 5 -> "V"
			| 6 -> "VI"
			| 7 -> "VII"
			| 8 -> "VIII"
			| 9 -> "IX"
			| _ -> invalid_arg "conv_units: not a digit" 
			in
			
		x4^x3^x2^x1

else 
	failwith"no one ever told you life was gonna be this way...." ;;
```

------

## TP

## exercise 5 

```ocaml
let rec f x = if x >= 1000 then 
let x_fl = float_of_int(x) and
	str_x = string_of_int(x) in
let chr1 = int_of_string(Char.escaped str_x.[0]) and
	chr2 = int_of_string(Char.escaped str_x.[1]) and
	chr3 = int_of_string(Char.escaped str_x.[2]) and
	chr4 = int_of_string(Char.escaped str_x.[3]) in
if chr1 = chr2 && chr3 = chr4 then 
	if float_of_int(int_of_float(sqrt(x_fl)))=sqrt(x_fl) then 
	let s = x 
	else 
		f (x-1)
else
	f (x-1)
```

------

## exercise 6 

```ocaml
let f x = let e_1 = x-5000 in
if e_1 > 99 && e_1 > 1000 then 
let e_2 = (e_1*1000)+e_1 in
let e_3 = (e_2/7)-(7*(e_2 mod 7)) in 
let e_4 = (e_3/11)-(11*(e_3 mod 11)) in 
let e_5 = (e_4/13)-(13*(e_4 mod 13)) in
if e_5 = 555 then 
	1
else 
	failwith"not the right number my dude"

```



------



# Homework

## exercise 4.2

```ocaml
let rec f n =
if n = 0 then
	0
else 
	4 * f(n-1)+2
```

## exercise 4.3 

```ocaml
let rec f n u q =
if n = 0 then 
	u
else 
	q*(f (n-1) u q)
```

## exercise 4.4

```ocaml
let rec gcd x y =
if y = 0 then 
	x
else 
	gcd (y-1)
	x mod y
```

## exercise 4.5 

```ocaml
let rec add x y =
if x = 0 then 
	(if y = 0 then 
		0
	else 
		add x (y-1))
else
	add (x-1) y 
	x+y
```

## exercise 4.6

```ocaml
let rec f x y = 
if y = 0 then 
	0
else 
	f (x-1) (y)
	x+x
```

## exercise 4.7

```ocaml
let x = 0 (* This would be our y counter *)
let rec euclid x y = 
	if x = 0 then
	(* 
	what i think we have to do here is remove y from x n times, until the remainder 	is above 0 but removing more would make it fall below 
	*)
	(*I have no idea ho to check for that however*)
	else
		euclid (x-y) y 	(* in theory this would launch the recursion each time 								   substracting y from x, but we would need to have some kind						    of check if x is above 0 which i dont get *)
```

## exercise 4.8

```ocaml
let rec fib = function
  | 0 -> 0
  | 1 -> 1
  | n -> fib (n-1) + fib (n-2)
```

## exercise 4.9

I seriously tried but don't even know how that thing is a function...





