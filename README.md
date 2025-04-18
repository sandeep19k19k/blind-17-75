# blind-17-75
Coin change

Dynamic programming .
We use a dp[ ] list of length amount+1 . where each dp[i] is initially set to amount+1.  ( virtually impossible no.of coins )
(later we use min function , so we will anyhow modify the result).
dp[0]=0.

i.e 0 is the minimum no.of coins required to build '0' amount.

i.e dp[i] represents the minimum no.of coins required to build 'i' amount.

and we build the dp[ ]  list as we iterate along from 1 to amount.

Can be better understood using an example.
Let's say we want to build 24.
and available coins =[3,4]
now do (24-3)=21.  If we somehow find out min no.of coins required to build 21, add 1 to that , and voila we found the answer.
Now again for 21 do the same thing . It's like a chain.
And hence we build the dp list linearly from i=0 to i=amount.
bcoz , we never know which value we might use later.
i.e it depends on coins given to us.

To put more clearly, for 24 , we needed dp[21] because the coins were [3,4].
If the coins were [4,8] , we would have needed dp[20] .

Hence dynamically keep track of all the possibilities, we might need later on based on given coins .
The key concept is,
for i in range(1,amount+1):
       for coin in coins:
              if i>=coin:
                   dp[i]= min(dp[i], dp[i-coin] +1)
return dp[amount]

Time complexity: O(amount* len(coins))
Space complexity: O(amount) 
