# caml seminar 

---

## exercise 3.5 

### 1

the first function takes an int as input and outputs an int. if the input is 1, the output will also be one but if the input is any other integer, it outputs 0, because of the first parameter in the case of x = 0, but due to rounding down any calculations made by the second pattern match in any other case.

### 2 

to eliminate the error, we must add a third match case, in the form of : 

``` ocaml
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



---

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

``` ocaml
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

---

## exercise 3.7

### 1 

``` ocaml
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

---

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

