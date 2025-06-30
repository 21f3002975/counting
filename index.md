---
layout: default
title: "Lets Count"
mathjax: true
---

# Counting with Stories

## The Story of Counting: From Pebbles to Probability

Long before equations, calculators, or even written language, humans were counting.
<br><br>
Imagine a shepherd, thousands of years ago, watching over his flock in the fading light of dusk. With no numerals or notations, he dropped a pebble into a pouch for every sheep that wandered past his hut at night. The next morning, he poured the pebbles out and, one by one, matched them to the sheep leaving the pen. If one pebble remained, he knew a sheep was missing. This wasn’t math as we think of it—but it was counting in its most primal form: a method to track, compare, and reason.
<br><br>
Over time, fingers gave way to tally marks etched on bones and stones. As trade and civilizations grew, so did the complexity of counting. The Egyptians tracked harvests, the Babylonians devised base-60 counting systems, and merchants used tokens and abacuses to track inventories and debts.
<br><br>
But counting wasn’t just about keeping track. It became a tool for exploring possibilities.

### The Rise of Structured Counting

At the turn of the first millennium, scholars began to ask deeper questions:  
*“In how many ways can you arrange objects?”*  
*“What happens if repetitions are allowed?”*  
These questions gave birth to early theories of permutations and combinations— the building blocks of what we now call combinatorics.
<br><br>
Centuries later, in 1700s Europe, minds like Blaise Pascal and Pierre de Fermat formalized counting in the context of uncertainty. Their letters back and forth laid the foundation for probability theory—a revolutionary idea that chance could be measured, predicted, and even calculated.
<br><br>
Counting, once a shepherd’s survival skill, had become a scientific discipline.

### From Enlightenment to Algorithms

As the world entered the era of reason and then computation, counting evolved again. It became abstract—rooted in algebraic structures and functions. Mathematicians developed:
<ul style="margin-left: 2em;">
  <li>Generating functions to encode sequences</li>
  <li>Partitions to explore sums of integers</li>
  <li>Set theory and group theory to analyze symmetry and structure</li>
</ul>

In the 20th and 21st centuries, counting took on new forms through statistical physics and computer science. Combinatorics now powers everything from quantum state calculations to AI search algorithms, from data compression to genome sequencing.


## Notation

Before we dive into counting techniques, here’s a quick reference for some standard mathematical notations used throughout this page:

<ul>
  <li>
    <strong>Factorial</strong>:  
    \( n! = n \times (n - 1) \times (n - 2) \times \cdots \times 1 \)  
    <br><em>Said as “n factorial”.</em> It represents the number of ways to arrange \( n \) distinct items in order.
  </li>
  <li>
    <strong>Permutations</strong>:  
    \( {}^nP_r = \dfrac{n!}{(n - r)!} \)  
    <br><em>Said as “n permute r”.</em> It counts the number of ordered arrangements of \( r \) items chosen from \( n \) distinct options.
  </li>
  <li>
    <strong>Combinations</strong>:  
    \( {}^nC_r = \dfrac{n!}{r!(n - r)!} \quad \text{or} \quad \binom{n}{r} \)  
    <br><em>Both are said as “n choose r”.</em> This gives the number of ways to choose \( r \) items from \( n \) distinct options <strong>when order does not matter</strong>.
  </li>
</ul>

## Counting, Probabilities and Uncertainity

As counting matured into a mathematical discipline, it became a foundation for understanding uncertainty—giving rise to the fields of probability and statistics. Before we can assign probabilities to outcomes or reason about randomness, we must first know how to count the possible arrangements or selections that underlie those outcomes. 
<br><br>
In **probability**, counting provides a way to calculate the likelihood of events. Probabilities are defined as ratios:

$$
P(A) = \frac{\text{Number of favorable outcomes}}{\text{Number of possible outcomes}}
$$

This simple formula relies entirely on accurate counting. Whether you're computing the odds of drawing a full house in poker or determining the chance of flipping 3 heads in 5 coin tosses, counting is indispensable. As problems get more complex, so does the need for structured counting models.

### Order and Replacement

Before we begin counting, we must ask ourselves the question: What exactly are we counting? More specifically, we are concerned with
<br><br>
**Order** - Are we counting simply the number of combinations of outcomes or their arrangements as well? 
Consider **flipping two coins**, is there a difference between the outcomes **(tails, heads) and (heads, tails)**? If order matters then they are not the same.
<br><br>
**Replacement** – Does choosing an item remove it from future selections, or is it still available? Does it affect the possible outcomes of subsequent events? 
<br><br>
Imagine you're selecting a **book to read from a digital library app** that has 3 featured books on the homepage. Each time you open the app, you're allowed to choose one of the books to read for a while and then return it. Since the books are digital and nothing is physically removed from the collection, you can choose the same book again later. This is a situation with **replacement**—each selection doesn't change the set of available options for the next round.
<br><br>
Compare that to a physical book fair, where if you pick a book and take it home, it's no longer on the shelf. The remaining options shrink after each selection—that's **without replacement**.
<br><br>
Answering these two questions on order and repitition yields 4 separate categories of counting problems,


| Model | Replacement | Order Matters | Example |
|-------|-------------|----------------|---------|
| 1. Ordered with Replacement | Yes | Yes | Setting a 4-digit PIN (digits can repeat) |
| 2. Ordered without Replacement | No | Yes | Assigning top 3 race positions from 10 runners |
| 3. Unordered without Replacement | No | No | Choosing 5 cards from a deck (e.g., poker hand) |
| 4. Unordered with Replacement | Yes | No | Selecting 3 scoops of ice cream (order irrelevant) from 5 flavors |


## A Short De-tour First

Prior to getting into each counting problem and its solutions, let us take a quick detour and learn a powerful tool to solve counting problems in general. This is particularly useful in combinatorics. It is called the **Story Proof** !

### The Power of Story Proofs in Counting

When faced with a complex-looking combinatorial identity, it’s tempting to dive straight into algebra: expanding factorials, simplifying expressions, and trying to manipulate your way to a solution. But in combinatorics, there's a different, often more intuitive technique—**story proofs**, also known as **combinatorial arguments**.

### What is a Story Proof?

A story proof doesn’t rely on manipulating symbols. Instead, it relies on **understanding what the expression actually counts**, and then telling a different “story” that counts the same thing in another way.
<br><br>
At its heart, a story proof answers the question:
<br><br>
> *Can I interpret both sides of this identity as counting the same thing, but from different perspectives?*
<br><br>
This approach not only simplifies many problems, but often reveals *why* an identity is true—something that pure algebra may obscure.


### Vandermonde's Identity 

### The Identity

$$
\sum_{j=0}^k \binom{m}{j} \binom{n}{k - j} = \binom{m + n}{k}
$$

At first glance, this looks intimidating—an unfamiliar summation of products of binomial coefficients. But with a good story, it becomes beautifully clear.

### The Story

Suppose you have two groups:
<br><br>
**Group A** has **m** people
**Group B** has **n** people

Together, there are **m + n** people. Now, you want to form a **committee of k people** from this combined group. That’s what the **right-hand side** is doing:

### The Right-Hand Side
Choosing **k people** from **m+n** people is what the right-hand side is doing. 

$$
\binom{m + n}{k}
$$

But now, let’s count the same thing a different way.

### The Left-Hand Side

Let’s decide **how many people to pick from Group A** and how many from Group B. Suppose we pick **j people from Group A**. Then, we must pick **k - j people from Group B** to reach k total.
<ul style="margin-left: 2em;">
  <li>Number of ways to choose j people from Group A: \( \binom{m}{j} \)</li>
  <li>Number of ways to choose k - j people from Group B: \( \binom{n}{k - j} \)</li>
</ul>

Now sum over all possible values of j (from 0 to k), and you’ve accounted for **every way to form a k-person committee from two groups**, by considering all possible combinations of contributions from Group A and B.
<br><br>
That’s exactly what the **left-hand side** is doing:

$$
\sum_{j=0}^k \binom{m}{j} \binom{n}{k - j}
$$

### Why This Matters

Algebraically, proving this identity is messy—it requires manipulating binomial coefficients and careful bookkeeping. But the story proof is:
<ul style="margin-left: 2em;">
  <li>Clean </li>
  <li>Visual</li>
  <li>Intuitive</li>
</ul>

And most importantly, it shows *why* the identity is true—not just *that* it is.
<br><br>

Story proofs like this are a central technique in combinatorics because they link **counting** to **context**. They turn numbers into narratives—and in doing so, reveal patterns that algebra alone might hide.

## The Big Four

Now let us get back to the main focus of our article.
<br><br>

Thus far, we have seen that answering the below two questions, helps us categorize the counting problems into 4 sub-categories.
<ul style="margin-left: 2em;">
  <li><strong> Does order matter? </strong></li>
  <li><strong> Are repetitions allowed? (replacement of chosen items) </strong></li>
</ul>

And the solutions to these **four counting problems**are as follows:

|                       | Order Matters               | Order Doesn't Matter   |
|-----------------------|-----------------------------|------------------------|
| **With Replacement**  | $$ n^k $$                   | $$ \binom{n + k - 1}{k} $$ |
| **Without Replacement** | $$ \frac{n!}{(n - k)!} $$ | $$ \binom{n}{k} $$ |

Where:

<ul style="margin-left: 2em;">
  <li> \( n \) = total number of distinct items</li>
  <li> \( k \) number of selections</li>
</ul>

---

## Details of each Counting method

While building the algebric solutions for each counting problem, we will use story proofs where required.

Imagine you've downloaded a new app that requires you to set a 4-digit PIN. How many different PINs can you create? For simplicity, let’s restrict the options to 10 digits: 0, 1, 2,... 9. 

But before starting to solve it, spend a minute thinking of those two questions - **1) Does order matter? 2) Are repititions allowed?** The answer to the first one is yes order matters. In case of the latter, it usually depends on the application. In some case they may restrict repitition. In our case let us assume that repitition is allowed. And this takes us to our first category of counting problems.

### 1. **Ordered with Replacement**

The standard way of phrasing this set of counting problems is : in how many ways can I choose \( k \) items from \( n \) choices, when order matters and replacement is allowed?
<br><br>
Going back to our password example. We have 4 positions to fill from 10 choices: \( 0, 1, 2...9 \), and we can look at the choice for each position as an individual event with 10 different outcomes (corresponding to the 10 digits).
<ul>
  <li>For position 1, we can thus count 10 possible outcomes.</li>
  <li>
    What about for position 2? As our choice for position 1 is not consumed, we can choose the same digit again – or we can choose a different digit. We still have 10 possible outcomes – and we count these 10 outcomes for each different outcome from position 1.
  </li>
</ul>
<p>We can now write the overall \( 10 \times 10 \) ways of making a choice. Continuing this, we get \( 10^4 = 10,000 \) choices for the 4-digit PIN.</p>
Now generalize this argument for \( k \) positions with \( n \) choices for each position. We are choosing \( k \) items from \( n \), and every item can be chosen again.

<ul style="margin-left: 2em;">
  <li>Each of the \( k \) positions has \( n \) choices</li>
  <li>\( n \times n \times \cdots \times n = n^k \)</li>
</ul>

<br><br>
**Below is a simulation for illustration, go ahead tinker with it.**
<br><br>

<iframe src="/visualizations/ordered-replacement.html" width="100%" height="450" style="border: 1px solid #ccc; border-radius: 8px;"></iframe>


### 2. **Ordered without Replacement**

The standard way of phrasing this set of counting problems is : in how many ways can I choose \( k \) items from \( n \) choices, when order matters and replacement is not allowed?
<br><br>
Suppose 10 runners have a race and we need to award first, second and third prize. We might award the first prize to any of the 10 but for second prize, we can now only count up to 9 choices – it makes no sense to award second prize to the first-prize winner as well, so we take him out of the selection and we are left with 9 candidates. We thus have 10 * 9 =90 possible outcomes of the race where we award 2 prizes, and by extension 10 * 9 * 8 = 720 possible outcomes where we award 3 prizes.
<br><br>
<p>Now extend this to \( k \)  positions with \( n \) participants. The 1st position has $n$ choices of winners, the 2nd has \( n-1 \), the 3rd one has \( n-2 \) and for the (\ k^{th} \) position it will be \( n-k+1 \).
So that total options will be \( n \times (n-1) \times \ldots (n-k+1) \). Multiply this with \( (n-k) \times (n-k-1) \ldots \times 1 \) on the numerator and denominator to get the expression,

$$ 
P(n, k) = \frac{n!}{(n - k)!} 
$$
</p>

**Below is a simulation for illustration, go ahead play around with it.**
<br><br>

<iframe src="/visualizations/ordered-no-replacement.html" width="100%" height="450" style="border: 1px solid #ccc; border-radius: 8px;"></iframe>


### 3. **Unordered with Replacement**

Suppose we want to choose \( k \) items from a set of \( n \) distinct items. This time, we are allowed to **repeat selections** (replacement is allowed), but **we don’t care about the order** in which the items are chosen.
<br><br>
This situation might sound tricky at first, but there's a very helpful way to visualize it: using **stars and bins** (also called the **stars and bars** method).

#### A Different Way to Think About It - The Stars and Bars Perspective

Instead of thinking about *choosing items*, imagine we are **distributing \( k \) identical stars into \( n \) distinct bins**.

<ul style="margin-left: 2em;">
  <li>Each <strong>star</strong> represents one selection.</li>
  <li>Each <strong>bin</strong> represents one of the \( n \) available items.</li>
  <li>Since we can place multiple stars in the same bin, we're allowing <strong>repetition</strong> (i.e., selection with replacement).</li>
  <li>Since the stars are identical, we’re only interested in <strong>how many stars end up in each bin</strong>, not the order they were placed — making this <strong>unordered</strong>.</li>
</ul>

This reframes our problem as:
> In how many ways can we place \( k \) identical stars into \( n \) labeled bins?

#### Stars and Bars: The Trick

To solve this, we can imagine arranging all the stars in a line, and then inserting **dividers (bars)** to split them into bins.

<ul style="margin-left: 2em;">
  <li>We have \( k \) stars.</li>
  <li>To divide them into \( n \) bins, we need \( n - 1 \) bars.</li>
  <li>So we are arranging \( k + (n - 1) = n + k - 1 \) symbols in total — a mixture of stars and bars.</li>
</ul>

Each unique arrangement of these \( n + k - 1 \) symbols represents a valid way to distribute the stars into bins.


#### The Counting Step

Now comes the clever part:  
To count the number of such arrangements, we simply need to **choose \( k \) positions for the stars** (or equivalently, \( n - 1 \) positions for the bars) from the \( n + k - 1 \) available slots.

$$
\text{Number of ways} = \binom{n + k - 1}{k}
$$

This is the total number of ways to choose \( k \) items from \( n \) types, **with replacement** and **without considering order**.

#### Real-World Analogy

Imagine you have \$100 that you want to break into bills of certain denominations: \$50, \$20, \$10, and \$5. Your goal is to find out **how many different ways** you can split the \$100 using any number of these bills — as long as the total is exactly \$100.

Here, each **denomination** (\$50, \$20, \$10, \$5) acts like a **bin** (or category), and each time you choose a bill, you're placing a **star** into that bin.

<ul style="margin-left: 2em;">
  <li>You can choose the same denomination multiple times — just like <strong>replacement</strong> in our model.</li>
  <li>You don’t care about the <strong>order</strong> in which the bills are chosen — only <strong>how many</strong> of each you end up with.</li>
</ul>

This is exactly the kind of problem stars and bars was designed for:  
> You are distributing a fixed number of identical items (dollar value in this case) across a fixed set of labeled categories (bill types), allowing repeats, and ignoring order.

<p>If we translate this into math: you're counting how many integer solutions exist to an equation like:

$$
50x + 20y + 10z + 5w = 100
$$

under the constraint that \( x, y, z, w \geq 0 \) and are integers. This is a **partitioning problem**, and while solving it exactly involves a bit more than stars and bars (because of coefficients), the underlying counting structure is very similar: you're placing indistinct units (stars) into labeled bins (bill types), with repetition and without caring about order.
</p>
<br><br>
**Below is a simulation for illustration, go ahead and try it**
<br><br>

<iframe src="/visualizations/unordered-replacement.html" width="100%" height="450" style="border: 1px solid #ccc; border-radius: 8px;"></iframe>


### 4. **Unordered without Replacement**

Suppose you're forming a **committee of 3 people from a group of 10**. The key condition is that **there are no roles, titles, or ranks** — every member of the committee is treated equally. This means that the **order in which you select them doesn't matter**.
<br><br>

<p>Let’s first walk through what happens <strong>if we did care about order</strong>:</p>
<ul style="margin-left: 2em;">
  <li>For the first position, we have 10 choices.</li>
  <li>For the second, 9 remaining choices.</li>
  <li>For the third, 8 choices.</li>
</ul>

<p>
  That gives us \( 10 \times 9 \times 8 = 720 \) different <strong>ordered</strong> outcomes. But in this committee scenario, choosing (Alice, Bob, Carol) is <strong>the same as</strong> (Carol, Bob, Alice) — they all lead to the same group of people. So these 720 outcomes <strong>overcount</strong> what we actually want.
</p>

To correct for this, we need to ask:  
> How many different ways can we reorder a single 3-person group?

The answer is \( 3! = 6 \) — every group of 3 people appears **six times** in the ordered list (once for each possible ordering).

So to find the number of **unordered** selections, we divide out the redundancy:

$$
\frac{10 \times 9 \times 8}{3!} = \frac{720}{6} = 120
$$

In general, when choosing \( k \) items from \( n \), and:
<ul style="margin-left: 2em;">
  <li><strong>Order does not matter</strong></li>
  <li><strong>No item is reused</strong> (no replacement)</li>
</ul>

We start with the total number of ordered selections (as in permutations), which is:

$$
\frac{n!}{(n - k)!}
$$

But since each group of \( k \) items appears \( k! \) times (once per permutation of those items), we divide by \( k! \) to eliminate overcounting:

$$
\binom{n}{k} = \frac{n!}{k!(n - k)!}
$$

This is called a **combination**, or more informally, **“n choose k”**. It gives the number of ways to choose \( k \) items from \( n \), **ignoring order and without replacement**.

<br><br>
**Below is a simulation for illustration, go ahead and play around with it**
<br><br>

<iframe src="/visualizations/unordered-no-replacement.html" width="100%" height="450" style="border: 1px solid #ccc; border-radius: 8px;"></iframe>


## Parting Thoughts

The four counting models we've explored — whether or not **order matters**, and whether or not we allow **replacement** — form the backbone of countless problems in combinatorics, probability, computer science, and even the real world.

Through these models, we’ve learned to:
<ul style="margin-left: 2em;">
  <li>Break complex decisions into simple, repeatable rules.</li>
  <li>Visualize problems using powerful metaphors like slots, bins, and stars.</li>
  <li>
    Translate abstract questions into mathematical formulas:
    \( n^k \), \( \dfrac{n!}{(n - k)!} \), \( \binom{n}{k} \), and \( \binom{n + k - 1}{k} \).
  </li>
</ul>

Understanding these distinctions isn't just about solving textbook problems — it's about recognizing structure in everything from PIN codes and passwords to elections, inventory tracking, and resource allocation.

In short: **Before you can measure chance, you must know how to count.**
<br><br>

---

<span style="font-size: 0.9em; color: #555;">
This content was developed and compiled as part of a learning project exploring foundational ideas in combinatorics and probability for the <em>Discrete Mathematics ES214</em> course at IIT Gandhinagar.<br>
<span style="font-size: 0.9em; color: #777;">
Credits: Some of the content has been inspired by: Joe Blitzstein’s lecture series on probability and statistics at Harvard.
</span>
</span>