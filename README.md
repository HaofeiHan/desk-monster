# Desk Monster

A desk pet that eats your finished to-dos.

Desk Monster turns a Raspberry Pi 4B into a small desktop companion. Instead of a plain to-do list, you take care of a little on-screen monster: every task you complete earns points, and you spend those points on food and treats to keep your monster fed and happy.

## How it works

1. Tell the monster what you need to do in plain language, like "finish the report by Friday, it's urgent." It turns that into a task with a deadline and a priority.
2. If a task is big or vague, the monster can break it into a few smaller steps. Each step earns its own points, so progress shows up sooner.
3. Give a rough time estimate. The monster compares it with how long similar tasks actually took you before, and suggests a more realistic one.
4. Start the timer when you begin a task and stop it when you're done. If you forget, just pick roughly how long it took when you check it off.
5. Complete tasks to earn points, then spend them on food and care items for your monster.
6. The monster reacts to how your day is going. It gets happy when you make progress, hungry when you don't, and worried when today's plan is more than you usually get done in a day.

## Role of the language model

- **Task capture:** turns natural-language input into structured tasks (title, deadline phrase, priority) as grammar-constrained JSON. Dates are calculated in code.
- **Task breakdown:** splits big or vague tasks into a few concrete steps.
- **Task matching:** tags each task with a category, so a new task can be compared with similar past ones.
- **Personality:** writes what the monster says, reacting to your actual progress, such as finishing a hard task, putting something off for days, or overloading your day.

The model does not guess time estimates. The built-in timer records how long each task actually takes, and the device compares that with your original estimate to learn how much you typically under- or over-estimate each kind of task. New estimates are adjusted to match. The more tasks you complete, the more accurate the estimates become. The device also tracks how many hours of work you actually finish per day, so it can flag plans that won't fit. The model only puts these results into the monster's voice.

Game logic (points, hunger, mood, timer) and all estimation math stay in regular code.

Planned approach: a ~1B-parameter quantized model via llama.cpp on a Pi 4B (4GB), with short structured outputs. To work around the Pi's limited speed, lines are pre-generated and cached while the device is idle.

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
