# Creator Royalties

This is an extremely rough draft formatted in tweet-thread style. I will likely convert it to a long-form post format to later be summarized in tweets. Forgive me for the bad formatting.


We have 

1. Main Thread 
 - overview of question
 - quote tweet "*Can* We enforce creator royalties?"   aka Thread A
 - quote tweet "*Should* we enforce creator royalties?"   aka Thread B

### Main Thread

1/ On Enforcing Creator Royalites  (Endgame)

2/ We will explore this topic with two main questions:

(1) *Can* creator royalties be enforced, without trading off decentralization/censorship-resistance? 

(2) *Should* creator royalties be enforced?

 
(Maybe Quote Tweets)

3/ Question (1)

*quote A*

4/ Question (2)

*quote B*

### Thread A (Can we)

1/ Solving the Royalty Trilemma

Can creator royalties be enforced at the contract level?  

Can this enforcement avoid a compromise on Censorship-Resistance or Turing-Completeness?

* Trilemma Image *



2/ Can creator royalties be enforced at the contract level? Yes

As Zhouzun mentioned in the podcast, previous solutions have been made available. However, these solutions required mutable contracts.

One example is a a contract which blurs the nft image (alters the metadata) if it has been seen to avoid royalties. 

All variants of this approach are fundamentally equivalent to simply blacklisting the owner/item which avoided fees - they forfeit censorship-resistance and/or immutability.

We believe these are suboptimal. 



3/ This leaves us at the second question:

Can this enforcement avoid a compromise on Censorship-Resistance or Turing-Completeness?

@haseeb says this inevitably leads to a trilemma. 



4/ At the core of this trilemma lie two fundamental problems.

FP1) There is no way of discerning between a sale and a transfer at the contract level.

FP2) In the event of a sale, how does the contract determine the *true* value of the sale?



5/ FP1: Discerning between a transfer and a sale... What does this mean?

Imagine your contract has two functions: `transfer(recipient)` and `sale(buyer, saleAmount)`

In this case, predatory marketplaces *cough ME* can conduct sales with the `transfer()` function, escrowing the sale proceeds externally.



6/ There are two approaches to solving this issue. The first is to utilize higher-level technologies much like that of @MatricaLabs, such that users have the option to self-identify their wallets if they want to avoid royalty payments for intra-person transfers.

This would allow the contract to check if the recipient implies an intra-person transfer (i.e. burner wallet to ledger)

Pseudo Logic:

```python
if recipient is in MatricaUser(nft.Owner).RegisteredWallets:
    transfer
else:
    requireRoyalty
```

7/ Although this seems like it compromises on censorship, the mechanism is opt-in. There is no requirement to doxx wallets. Additionally, the higher-level wallet-link application can utilize cryptographic solutions like simple encryption, or even ZK-Proofs, to protect the user's information.



8/ Second, we have the more trivial solution: Treat *every* transfer as if it was a sale. This does mean that a user would have to pay royalties in the scenario where they want to transfer from a burner to a ledger, but it preserves privacy, censorship-resistance, decentralization, and everything else we love about blockchains.

Aka instead of having `transfer(recipient)` and `sale(buyer, saleAmount)`, we only have the latter.

Now we must address FP2) How much royalty, exactly, is owed?



9/ If we naively implement this as x% of the `saleAmount`, then we again allow a predatory marketplace to avoid these fees. They simply call the function ``sale(buyer, saleAmount)` with saleAmount == 0.01 Sol, and escrow the rest of the *true sale* externally.

Again, there are two solutions.

1) Use an Oracle as a source of truth (floor price, recent sale, etc. The implementation is up to the oracle)
2) Require a fixed price royalty: 1 SOL, 40 USDC, or an option between a list of `(token, amount)` pairs (effectively the minimum option)

TODO expand on this? Seems trivial to me, does it need further explanation?



10/ Some conclusion TODO




### Thread B (Should we)

0/ Should creator royalties be enforced?


1/ There was a fruitful debate around this question in the recent podcast Co-Hosted by @LauraShin (@Unchained) and @Haseeb (@Choppingblock), with guests @ZhouxunYin, CoFounder of @MagicEden, and @Li Jin, CoFounder of @variantfund

The summarize the viewpoints, 

Laura and Li sided with "yes" 
Haseeb and Zhouzun sided with "No"



2/ Before discussing our view, we think it's necessary to steelman each side of the argument.

First, why creator royalties should be enforced:



3/ Royalties ~ should ~ be enforced because 

 - Royalties financially support the creator. They allow the creator to yield value in perpetuity, from the asset/collection which they created.
 - A failure to enforce royalties will disincentivize creator participation in Web3. In the long run, this harms everyone, including the buyers/speculators.



4/ Royalties ~ should not ~ be enforced because

 - Royalties account for a small (and decreasing) portion of total creator compensation.
 - An artist can profit from (expected) future success without royalties, instead opting to withold a portion of the supply for later primary sales.



5/ Of course, these are oversimplfied recommendations of each side of the argument. We recommend listening to the conversation in full, which can be found here.

Now let's discuss our view.

(LINK)



6/ Ape16z believes in permissionlessness, decentralization, and censorship-resistance.

We believe the right to decide whether to enforce royalties at the contract level is up to the project/creator.

In other words, the project/creator should have the right to enforce royalties, if they want to.
Likewise, the buyer should have the right to prefer creators that omit royalties, if they want to.

Allowing each side to take course will inevitably let the market to decide which approach is superior.



7/ This begs the question: *Can* we enforce creator royalties?

(QUOTE THREAD B)

