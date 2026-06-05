# Gothic Remake Chest Solver

Small browser-only solver for the Gothic Remake chest/lock puzzle.

- **Runs 100% in the browser** (no installs)
- Supports up to **6 disks**
- Uses **BFS** to find the **shortest** solution (fewest moves)

## Live Demo

[https://nutschulk.github.io/GothicRemakeChestSolver/](https://nutschulk.github.io/GothicRemakeChestSolver/)

## How to use

### 1) Choose number of disks

Set **Number of disks** to your puzzle size (max 6).

### 2) Enter the start state

The **Start** field is the current pin positions for each disk.

- Values are **1..7**
- **1 = left-most pin position**
- **7 = right-most pin position**

Example (5 disks):

- `1,3,1,1,3`

### 3) Enter the coupling rules

Rules are entered one line per disk (using disk numbers **1..N**):

```
1: 2+, 3-, 5-
2: 4-
3:
4:
5: 3+, 4-
```

Meaning:

- When you move disk **1**, disk **2** also moves in the **same** direction (`2+`), disk **3** moves in the **opposite** direction (`3-`), and disk **5** moves in the **opposite** direction (`5-`).
- An empty line like `3:` means disk 3 has **no couplings**.

### 4) Movement convention (fixed)

This solver uses a fixed convention:

- Pressing **L** means the disk position changes by **+1**
- Pressing **R** means the disk position changes by **-1**

### 5) Solve and verify

- Click **Solve (shortest)** to get the move list.
- Click **Validate solution step-by-step** to simulate every move and print each intermediate state.

## How it works (short)

A puzzle configuration is represented as a tuple of pin positions, one per disk.

- A move selects a disk and applies `L` or `R`.
- The selected disk always moves.
- Coupled disks also move according to your rule signs (`+` same direction, `-` opposite direction).
- A move is invalid if any affected disk would leave the range **1..7**.
- BFS explores states level-by-level, so the first solution found is minimal in number of moves.

## GitHub Pages setup

Recommended setup:

1. Rename `gothic-lock-solver.html` to `**index.html**`
2. Commit &amp; push
3. In the repo: **Settings → Pages**
  - Source: *Deploy from a branch*
  - Branch: `main`
  - Folder: `/ (root)`

Your site will be available at:

- [https://nutschulk.github.io/GothicRemakeChestSolver/](https://nutschulk.github.io/GothicRemakeChestSolver/)

