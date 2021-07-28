# almost-reversed-2-lag-Markov-chain

Another simple riddle from the Riddler: take a binary sequence and associate to this sequence a score vector made of the numbers of consecutive ones from each position. If the sequence is ten step long and there are 3 ones located at random, what is the expected total score? (The original story is much more complex and involves as often strange sports!)

Adding two zeroes at time 11 and 12, this is quite simple to code, e.g.

f=0*(1:10) #frequencies
for(v in 1:1e6){
 r=0*f#reward
 s=sample(1:10,3)
 for(t in s)r[t]=1+((t+1)%in%s)*(1+((t+2)%in%s))
 f[sum(r)]=f[sum(r)]+1}
f=f/1e6

and the outcome recovers the feature that the only possible scores are 1+1+1=3 (all ones separated), 1+1+2=4 (two ones contiguous),  and 1+2+3=6 (all ones contiguous). With respective frequencies 56/120, 56/120, and 8/120. With 120 being the number of possible locations of the 3 ones.
