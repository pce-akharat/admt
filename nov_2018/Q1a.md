> Explain Brute-Force Nested Loop Join algorithm. [5M]
***

#### Brute-Force Nested Loop Join algorithm [1M]
This is a simple algorithm to compute the theta join between two relations R and S.
This algorithm is called the nested-loop join algorithm, since it basically consists of a pair of nested for loops. 
Relation R is called the outer relation and relation S the inner relation of the join, since the loop for R encloses the loop for S. 
The algorithm uses the notation tr · ts, where tr and ts are tuples; tr · ts denotes the tuple constructed by concatenating the attribute values of tuples
tr and ts .
#### Algorithm [2M]
```
for each tuple tr in R do begin
  for each tuple ts in S do begin
    test pair (tr, ts) to see if they satisfy the join condition theta
    if they do then add tr · ts to the result;
  end
end
```

#### Cost (Seeks, Black transfers) [2M]
br -> number of blocks of relation R  
bs -> number of blocks of relation S  
nr -> number of tuples of relation R  
ns -> number of tuples of relation S  
##### Seeks
We need only one seek for each scan on the inner relation S since it is read sequentially, and a total of br seeks to read r and therfore
```
Number of Seeks = br + nr  
```
##### Block transfers
For each record in R, we have to perform a complete scan on S. In the worst case, 
the buffer can hold only one block of each relation and therfore
```
Number of block transfers = br + nr * bs
```
