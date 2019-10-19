# haskell-exercise

# 1. (*) Exercises from chapter 9-10 of The Craft of Functional Programming
(*) Define the length function using map and sum. 

Answer:
Assume xs is 1-dimension list : 
sum (map (\_ -> 1) xs)

(*) What does map (+1) (map (+1) xs) do? Can you conclude anything in general about properties of map f (map g xs), where f and g are arbitrary functions?

Answer :
What map (+1) (map (+1) xs) do is mapping each element of xs to function named (+1), which add 1 to each element of xs, then we produce the new list. With this new list, we map again each element of xs to function named (+1), then we produce the new list again. 

The conclusion about properties of map f (map g xs) is we do composition function to each element of xs with mapping rule g, then produce new list, next we map again this new list with mapping rule f, then produce new list again. In math, we already familiar with this composition function notation as f o g (xs) or f(g(xs)).

# 2. (*) List Comprehensions and Higher-Order Functions
Can you rewrite the following list comprehensions using the higher-order functions map and filter? You might need the function concat too.

1. [ x+1 | x ← xs ]
2. [ x+y | x ← xs, y ← ys ]
3. [ x+2 | x ← xs, x > 3 ]
4. [ x+3 | (x,_) ← xys ]
5. [ x+4 | (x,y) ← xys, x+y < 5 ]
6. [ x+5 | Just x ← mxs ]

Answer :
1. map (+1) xs
2. concat (map (\x -> map (x+) ys) xs)
3. map (+2) (filter (>3) xs)
4. map (+3) (map fst xys)