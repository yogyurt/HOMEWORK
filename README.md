# Homework 

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
	match e_5 with
		| 555 -> true
		| _ -> false
else
	false


```

