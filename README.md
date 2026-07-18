# University-Science-game

# Sixty Second Seminar

A single-file HTML quiz game covering university-level science: Physics, Chemistry, Biology, Math, Astronomy, and Earth Science. Chalkboard aesthetic, 60-second rounds that auto-restart.

## How to run

No build step or server needed — the file is fully self-contained.

1. Download `sixty-second-seminar.html`.
2. Open it directly in any modern browser (double-click, or drag it into a browser window).

It uses Google Fonts over the network (Permanent Marker, Caveat, Space Mono, Inter) for the chalk/handwriting look, so an internet connection improves the visual, but the game still works offline with fallback fonts.

## How it works

- Answer as many multiple-choice questions as you can in 60 seconds.
- The circular clock and the bar underneath both count down together; both turn coral in the final 10 seconds.
- Score increases by 1 per correct answer; the correct choice is always revealed before moving on.
- When the timer hits 0, an eraser-wipe animation plays, your round score is compared to your best, and a fresh round starts automatically — no button press needed.
- **Copy button**: next to the subject tag on each question, tap **Copy** to copy the current question and its answer choices (labeled A–D) to your clipboard.

## Persistence

Your best score is saved between visits using the browser's artifact storage (`window.storage`), not `localStorage`, under the key `best-score`.

## Customizing

The question bank lives in a single `QUESTIONS` array near the top of the `<script>` block. Each entry looks like:

```js
{ tag: "Physics", q: "Question text?", choices: ["A", "B", "C", "D"], a: 1 }
```

- `tag` — the subject label shown above the question.
- `q` — the question text.
- `choices` — exactly four answer options.
- `a` — the zero-based index of the correct choice.

Add, remove, or edit entries to change the question bank. Choices are shuffled per question, so the position of `a` in the array doesn't affect difficulty.

To change the round length, update the two places `timeLeft = 60` is set. The clock ring's `CIRC` constant assumes a 60-unit countdown, so it will still track correctly as long as `timeLeft` starts at 60.
