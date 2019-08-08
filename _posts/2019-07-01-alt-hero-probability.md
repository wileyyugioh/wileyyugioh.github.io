---
title: Alternate Hero Probability
tags: info
mathjax: true
---

Happy three days until July 4th everybody! I just wanted to write a quick post about some probability number crunching I did a little while ago. The reason being that most websites I found did not demonstrate the technique I ultimately ended up using, and I feel that these probability problems come up often enough to justify writing it down.

The problem is as follows: let's say I'm opening boosters for a trading card game, and I want to collect specific rare cards A and B. Cards A and B have a 0.03% pull rate, meaning that each card in a booster has a 0.03% chance of being A and 0.03% chance of being B. If I open 80 cards, what's the probability I pull both A and B? 400 cards? N cards?

It kinda sounds like the [coupon collector's problem](https://en.wikipedia.org/wiki/Coupon_collector%27s_problem), but not quite.

To solve this problem, let's write down every single possibility when opening N cards.

- Don't pull A and Don't pull B (Neither A nor B are pulled)
- Pull A and Don't pull B (At least one copy of A is pulled, but none of B are pulled)
- Pull B and Don't pull A (At least one copy of B is pulled, but none of A are pulled)
- Pull A and Pull B (At least one copy of both A and B are pulled)

Ultimately, our goal is to find the probability of **Pull A and Pull B**. However, that number is pretty difficult to calculate by itself. An easier way is to calculate all the other probabilities and subtract it from 1. This works since we know the sum of the probabilities of every possibility is equal to 1.

Let's go step by step.

## Don't pull A and Don't pull B

This one is pretty easy. Since both A and B have a 0.0003 chance of being pulled, it means that every other card has a 0.9994 chance of being pulled (1 - 0.0003 - 0.0003 = 0.9994). 

Therefore, the chance of not pulling A nor B is

$$ 0.9994^N $$

## Pull A and Don't pull B/Pull B and Don't pull A

Intuitively, we expect that the probability of **Pull A and Don't pull B** and **Pull B and Don't pull A** to be the same since they both have the same pull rates. That means we only have to solve for one of the cases! Let's solve for **Pull A and Don't pull B**.

An example of a pattern that would conform to **Pull A and Don't pull B** is

```
A, Z, Z, ..., Z
where A represents card A
      B represents card B
      Z represents all other cards
```

What is the probability of this particular pattern?

Well, you just multiply the probabilities together, so it's

$$ 0.0003 * 0.9994 * 0.9994 * \ldots * 0.9994 $$

We can condense this into

$$ 0.0003 * 0.9994^{N-1} $$

Nice, we got one pattern! Now all we have to do is calculate the probability for every step, and sum it all up! But that takes a lot of time, so isn't there an easier way to calculate the probabilities? Let's check out another pattern to see if there are any recurring themes.

```
Z, A, Z, ..., Z
```

This has a probability of


$$ 0.9994 * 0.0003 * 0.9994 * \ldots * 0.9994 $$

Wait a minute, since the order of multiplication doesn't matter–this probability is the same as the previous pattern! That means we can deduce that the probability of pulling **one** A is the same no matter what order we pull the A! Since there are N possible combinations of forming a pattern with one A, that means the total probability for pulling one A is

$$ N * 0.0003 * 0.9994^{N-1} $$

Cool, let's do it with two A's.

```
A, A, Z, ..., Z
```

which has a probability of

$$ 0.0003 * 0.0003 * 0.9994 * \ldots * 0.9994 $$

which is equal to

$$ 0.0003^2 * 0.9994^{N-2} $$

But how many combinations do we have with two A's? It's not N anymore since introducing another A increases the number of patterns we can create. The number of combinations we can create with two A's is, as you may have guessed, [$ \binom{N}{2} $](https://www.mathsisfun.com/combinatorics/combinations-permutations.html).

This makes the total probability of pulling two A's

$$ \binom{N}{2} * 0.0003^2 * 0.9994^{N-2} $$

We can also rewrite the probability for drawing one A using the combination function as well

$$ \binom{N}{1} * 0.0003^1 * 0.9994^{N-1} $$

*Note: $ \binom{N}{1} = N $*

This pattern can be repeated over and over again until we have N A's, or every single card we pull is an A

$$ \binom{N}{N} * 0.0003^N * 0.9994^{N-N} $$

*Note: $ \binom{N}{N} = 1 $*

Sum up all the probabilities and we get the total probability for **Pull A and Don't pull B** to be

$$ \sum_{i=1}^N \binom{N}{i} * 0.0003^i * 0.9994^{N-i} $$

This equation also applies to **Pull B and Don't pull A**.

## Pull A and Pull B

Let's recap our known probabilities

- Don't pull A and Don't pull B: $ 0.9994^N $
- Pull A and Don't pull B: $ \sum_{i=1}^N \binom{N}{i} * 0.0003^i * 0.9994^{N-i} $
- Pull B and Don't pull A: $ \sum_{i=1}^N \binom{N}{i} * 0.0003^i * 0.9994^{N-i} $
- Pull A and Pull B: **???**

Since we know every other probability, solving for **Pull A and Pull B** is easy–we just subtract all the probabilities from 1.

This makes the probability of **Pull A and Pull B**, or pulling both A and B

$$ 1 - 0.9994^N - 2 * \sum_{i=1}^N \binom{N}{i} * 0.0003^i * 0.9994^{N-i} $$

where N is the number of cards pulled.

Phew!

## Plugging it in

Below are some probabilities I calculated

| N (# of cards) | P (Chance of drawing A and B) |
| -------------- | ----------------------------- |
| 2              | 1.8000 * 10^-7                |
| 80             | 5.5567 * 10^-4                |
| 400            | 1.2760 * 10^-2                |
| 4093           | 0.5000                        |
| 17650          | 0.9900                        |

That's a lotta packs!
