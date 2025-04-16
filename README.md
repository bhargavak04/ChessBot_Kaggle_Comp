# ♟️ ChessBot — A Heuristic Chess Engine with Minimax and Alpha-Beta Pruning

This project presents a classic yet effective chess-playing bot developed for the **Kaggle & FIDE ChessBot Competition**. The engine uses foundational AI algorithms such as **Minimax with Alpha-Beta Pruning**, enhanced by **heuristic evaluations** and **MVV-LVA (Most Valuable Victim - Least Valuable Attacker) move ordering**.

---

## 📌 Features

- **Minimax Algorithm** for intelligent decision-making.
- **Alpha-Beta Pruning** to reduce the search space.
- **MVV-LVA Move Ordering** to prioritize captures and improve efficiency.
- **Heuristic Evaluation Function** based on piece values.
- Lightweight and fast — no deep learning, just pure classic chess AI.

---

## 🧠 Algorithms & Techniques

### 1. Minimax with Alpha-Beta Pruning
A depth-limited search algorithm that simulates moves for both players, evaluating board positions to find the optimal move.

- **Alpha**: Best value the maximizer currently can guarantee.
- **Beta**: Best value the minimizer currently can guarantee.
- **Pruning**: Skips branches that won't affect the final decision, improving performance.

```python
minimax(board, depth, alpha, beta, maximizing_player)
```

### 2. Heuristic Evaluation Function
Evaluates a board position based on the material count using standard piece values:

```python
PIECE_VALUES = {
    chess.PAWN: 100,
    chess.KNIGHT: 320,
    chess.BISHOP: 330,
    chess.ROOK: 500,
    chess.QUEEN: 900,
    chess.KING: 20000
}
```

- Positive scores favor White, negative scores favor Black.
- Handles checkmate and stalemate detection.

```python
def evaluate_board(board):
    ...
    return score
```

### 3. MVV-LVA Move Ordering
Sorts legal moves based on capture priority — attacking high-value pieces with low-value ones:

```python
def mvv_lva(move, board):
    ...
    return value
```

This improves alpha-beta efficiency by evaluating more promising moves earlier.

---

## ⚙️ Dependencies

- `python-chess`
- `numpy`

Install with:

```bash
pip install python-chess numpy
```

---

## 🚀 Usage

This bot can be used within a game loop or plugged into a GUI/simulation environment. Here's a sample of how to make the bot play:

```python
import chess
import numpy as np

board = chess.Board()
while not board.is_game_over():
    if board.turn == chess.WHITE:
        _, move = minimax(board, depth=3, alpha=-np.inf, beta=np.inf, maximizing_player=True)
    else:
        _, move = minimax(board, depth=3, alpha=-np.inf, beta=np.inf, maximizing_player=False)
    board.push(move)
    print(board)
```

---

## 📈 Performance & Limitations

- **Strength**: Plays reasonable amateur-level chess. Best at tactics and fast evaluations.
- **Limitations**:
  - No positional evaluation (e.g., pawn structure, control of center).
  - No endgame or opening book.
  - Limited depth (usually 3-4 ply) due to lack of advanced pruning or transposition tables.

---

## 📚 Future Improvements

- Incorporate piece-square tables (PST) for positional scoring.
- Add quiescence search to avoid horizon effect.
- Implement opening databases or endgame tablebases.
- Parallelization or caching for better performance.

---

## 🏁 Competition Ready

This bot is lightweight and deterministic — perfect for controlled competition settings where fast, fair decision-making is essential.

---

## 🧑‍💻 Author

Developed by Bhargav AK for the **Kaggle & FIDE ChessBot Competition**.
