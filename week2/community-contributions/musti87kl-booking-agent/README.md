# Booking Agent (Week 2, Day 4)

A Gradio chat travel agent that quotes and books return flights by calling Python tools backed by a real SQLite database (`bookings.db`).

- `db.py`: creates the `PRICES` and `bookings` tables, plus 3 plain functions: `get_ticket_price`, `set_ticket_price` (upsert), `book_ticket` (reads the price from the DB, so the model cannot invent one; returns a `BK-<id>` reference).
- `tools.py`: the 3 JSON tool cards (`tool_cards`) and a name-to-function dict (`tool_functions`) instead of an `if` chain.
- `prompt.py`: the system prompt (ask the name, confirm before booking, only change prices for messages starting with `STAFF:`).
- `chat.py`: `handle_tool_calls` and the `while` loop, capped at `MAX_ROUNDS = 5`.
- `app.py`: `gr.ChatInterface`. Run `python app.py`.

Needs `OPENAI_API_KEY` in `.env`. Every tool call prints a spy line in the terminal, so you can watch the model order tools.
