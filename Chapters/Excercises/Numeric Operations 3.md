%% Fun fact: When this video dropped, I saw a lot of people trying to do this in the Python Discord server 
https://www.youtube.com/watch?v=094y1Z2wpJg 
%%

### Exercise 1 - Collatz

Use a while loop to calculate the Collatz sequence of a given input number, until it reaches `1`

$$
a_{n+1} = \begin{cases} {a_n} \div {2} & \text{if } a_n \text{ is even} \\ 3a_n + 1 & \text{if } a_n \text{ is odd} \end{cases}
$$

```py
start = int(input())
number = start
sequence = [number]

...

print(f"The sequence starting with {start} is: {sequence}")
```
