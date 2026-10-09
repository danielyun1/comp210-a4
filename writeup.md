# A4 Write-up

**Name: Daniel Yun**

**Onyen: dhyun1**

**Game URL:** https://bridges-cs.herokuapp.com/assignments/4/

**Bomb rule I played with (SHRINK or GAME_OVER): GAME_OVER**

Three questions, 20 points. A few sentences each. Where a question asks for a
number, show where it came from.

---

## Question 1: The tail pointer (7 points)

Your `LinkedQueue` keeps a `tail` reference. Suppose you deleted it and found
the back of the queue by starting at `head` and following `next` until you ran
out of nodes.

What would `enqueue` cost then, in Big-O? The game calls `enqueue` once per
tick and runs about 7 ticks a second. For a snake 500 cells long, roughly how
many nodes would `enqueue` alone visit each second, and would you notice?

Now do the same for the autograder's speed test. It fills a queue with
400,000 items, then does 400,000 more rounds of dequeue-then-enqueue, so the
queue stays at 400,000. Roughly how many nodes would those enqueues visit?

```
Enqueue would cost O(n). For a snake 500 cells long at 7 ticks a second, enqueue would visit 3,500 nodes a second and this would probably be unnoticable. For the autograder, it would be roughly 160 billion nodes visited which would be noticeable.
```

---

## Question 2: The one method allowed to walk (7 points)

`contains` is O(n), and the game calls it through `snake.occupies(...)`. Read
`GameState.tick()` and `GameState.freeCell()` and find every call.

On a tick where the snake eats an apple, roughly how many nodes do those
`contains` calls visit in total, for a snake of length n on the 30 by 30
board? Give an expression in n. Then name a data structure from later in this
course that would make "is the snake on this cell?" fast, and say what it
would cost to keep it up to date as the snake moves.

```
For a snake of length n on the 30 by 30 board, contains would call n + (30 x 30) * (n + 1). A data structure that would speed up the process would be a set and it would cost O(1) to keep up to date as the snake moves.
```

---

## Question 3: Which end is the head? (6 points)

The snake's head is the **back** of the queue, and its tail end is the
**front**. Explain why, using what happens to the body on each tick.

Then suppose you flipped it, so the head was the front. Which operation would
each tick need that `LinkedQueue` does not have, and why is that operation hard
to make O(1) on a singly linked list?

```
On each tick, the body enqueues a new head which adds a new head to the back of the queue. If it was flipped the head would be at the front of the queue and a new item would be enqueued to the front. However, each tick would need an operation that removes the node in the back of the queue which LinkedQueue does not have. That operation is difficult to make O(1) because the traversing through a singly linked list requires you to start at the head and going through each node from there.
```
