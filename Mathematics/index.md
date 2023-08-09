# 1 - MODULAR MATH

## 1.1 - Quadratic Residues

+ In Modular arithmetic we say number `x` is **Quadratic Residues** if there exists an `a` such that `a^2 = x mod p`. If there is no such solution, then the integer is a **Quadratic Non-Residue**.
+ Or the number `x` is **Quadratic Residues** if it is possible to take square root of `x` modulo `p`
+ For example which number in `[14, 6, 11]` is Quadratic Residues modulo `p=29`? find it and calculate it's square root

```
p = 29  
ints = [14, 6, 11]

it's 6:
8^2 mod 29 = 6
```


## 1.2 - Legendre Symbol

+ Legendre Symbols shows and prove that if a number is Quadratic Residues or Quadratic Non-Residues
+ Before looking at Legendre's symbol, let's take a brief detour to see an interesting property of quadratic (non-)residues.

Quadratic Residue * Quadratic Residue = Quadratic Residue  
Quadratic Residue * Quadratic Non-residue = Quadratic Non-residue  
Quadratic Non-residue * Quadratic Non-residue = Quadratic Residue

we can say Quadratic Residue is like `+1` and Quadratic Non-Residue is like `-1`

+ To show that a number is Quadratic Residue or Quadratic Non-Residue modulo an integer `p` just calculate this equations

```
Legendre Symbol (a / p) ≡ a**((p-1)/2) mod p
```

Legendre Symbol (a / p) = 1 if a is a quadratic residue and a ≢ 0 mod p  
Legendre Symbol (a / p) = -1 if a is a quadratic non-residue mod p  
Legendre Symbol (a / p) = 0 if a ≡ 0 mod p

+ Which means given any integer `a`, calculating `pow(a,(p-1)//2,p)` is enough to determine if `a` is a quadratic residue.

## 1.3 - Modular Square Root
 
 + In section 1.2 we mentioned an efficient way to determine if a number is Quadratic Residue or Quadratic Non-Residue
 + But here we wanna go further and find an efficient algorithm to calculate square root of a Quadratic Residue number modulo and integer `p`
 + The best one is called `Tonelli-Shanks`  algorithm
 + All primes that aren't 2 are of the form `p ≡ 1 mod 4` or `p ≡ 3 mod 4`, since all odd numbers obey these congruences.
 + If `p ≡ 3 mod 4` , a really simple formula for computing square roots can be [derived](https://crypto.stackexchange.com/a/20994) directly from Fermat's little theorem. That leaves us still with the `p ≡ 1 mod 4` case, so a more general algorithm is required.

## 1.4 - Chinese Remainder Theorem

+ The Chinese Remainder Theorem gives a unique solution to a set of linear congruences if their moduli are co-prime.
+ This means, that given a set of arbitrary integers `ai`, and pairwise co-prime integers `ni`, such that the following linear congruences hold:

 Note "pairwise coprime integers" means that if we have a set of integers `{n1, n2, ..., ni}`, all pairs of integers selected from the set are coprime: `gcd(ni, nj) = 1`.

```
x ≡ a1 mod n1  
x ≡ a2 mod n2  
...  
x ≡ an mod nn
```

There is a unique solution `x ≡ a mod N` where `N = n1 * n2 * ... * nn`.
for details you can watch this [video](https://www.youtube.com/watch?v=ru7mWZJlRQg&t=349s)


