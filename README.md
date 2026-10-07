# Desk Monster

A desk pet that eats your finished to-dos.

Desk Monster turns a Raspberry Pi 4B into a small desktop companion. Instead of a plain to-do list, you take care of a little on-screen monster: every task you complete earns points, and you spend those points on food and treats to keep your monster fed and happy.

## How it works

1. Add tasks to your list.
2. Complete tasks to earn points.
3. Spend points on food and care items for your monster.
4. The monster reacts to how your day is going, getting happy when you make progress and hungry when you don't.

## Role of the language model

A small language model running locally on the Pi gives the monster a personality. Instead of fixed canned messages, it reacts to your actual progress, such as finishing a hard task or putting something off for days. Game logic (points, hunger, mood) stays in regular code; the model only handles what the monster says.

Planned approach: a ~1B-parameter quantized model via llama.cpp, with short, structured outputs and pre-generated lines to work around the Pi 4B's limited speed.

## Hardware

- Raspberry Pi 4B (4GB)
- Small display (TBD)
- Input method (TBD: touchscreen, buttons, or phone web UI)

## Workstream

- **Week 7 (proposal):** concept, card, and feasibility check — run a small model on the Pi and measure speed.
- **Week 8–10 (work in progress):** task list, points and feeding system, monster personality prompts. Goal: a full loop of finish task → earn points → feed monster → monster reacts.
- **Week 10–15 (final release):** natural-language task input, visuals and animation, enclosure to make it a real desk object.

## Open questions

- Is the Pi 4B fast enough for real-time responses, or should most lines be pre-generated?
- Which display and input method fit a desk object best?

## AI collaboration

Developed with Claude (Anthropic) and ChatGPT (OpenAI).
