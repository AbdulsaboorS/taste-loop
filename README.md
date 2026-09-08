# Taste Loop

Taste Loop is an agent skill that turns an incomplete visual idea into a distinctive, verified product design.

It helps you discover what you want, researches relevant inspiration, turns your reactions into an explicit design direction, builds the product, and reviews the rendered result in a closed loop. The loop ends when the product passes its quality checks and feels valid to you.

## How it works

1. **Discover:** Inspect the project, learn your taste, research references, and explore distinct directions.
2. **Define:** Record the selected direction, implement it, capture the real product, and ask a fresh visual critic for specific feedback.
3. **Deliver:** Iterate by impact, inspect interactions and motion, remove what does not add value, and ask you to validate the result.

Taste Loop supports four modes:

- **Quick polish:** One focused improvement and review round.
- **Guided:** Up to three useful directions, decision checkpoints, and up to two review rounds. This is the default.
- **Full studio:** Broad research, comparative prototypes, and up to three review rounds.
- **Hands-off:** The agent makes the intermediate decisions and returns for final validation.

## Installation

Install with the Skills CLI:

```bash
npx skills add AbdulsaboorS/taste-loop
```

You can also place the repository folder in your client's personal or project skills directory. Installation paths and direct-command syntax vary by client; consult its Agent Skills documentation. A compatible agent can also discover the skill from a natural-language request matching its description.

## Usage

Invoke the skill directly:

```text
/taste-loop Redesign this dashboard. Keep it dense and operational, but make it feel calm and exceptionally well crafted. Use Guided mode.
```

Start from an incomplete idea:

```text
/taste-loop Full studio mode. I am building a reading app for long technical articles. I know I want it to feel focused and tactile, but I cannot describe the design yet. Help me find the direction before building it.
```

Request an autonomous run:

```text
/taste-loop Hands-off mode. Build a native-feeling personal finance app that makes weekly planning feel approachable rather than clinical. Use your judgment, verify every important interaction, and show me the finished result.
```

## Capabilities

Taste Loop needs an agent that can edit and run your project. Results improve when the agent also has:

- Web research for visual references.
- Vision and screenshot capture.
- Browser, device, or simulator control.
- A fresh subagent for independent criticism.
- Image or video generation when the design calls for it.
- Screen recording and frame extraction for motion review.

Rendered evidence and vision are required for a verified visual loop. If they are unavailable, Taste Loop asks for user-provided captures or offers a planning-only run. Other capabilities are optional, and the skill reports what it could not verify.

Image and video generation can incur API costs. Use narrowly scoped development keys through environment variables. Do not place credentials in prompts, source code, or committed files. Taste Loop requests consent before sending private project material to an external model or media service and directs the agent to redact sensitive content.

## Design references

Depending on the product, Taste Loop may research Mobbin, Refero, Page Flows, Screenlane, Awwwards, SiteInspire, Land-book, Godly, One Page Love, Dribbble, Behance, Are.na, platform guidance, studio portfolios, and relevant working products.

References establish principles and a quality bar. They are not templates to copy.

## Status

Taste Loop is an early experiment. It currently targets skills-compatible coding agents and has not yet been tested across every supported agent or project type.

If you contribute a change to the workflow, include an example result or evaluation that shows why the change improves outcomes without regressing another mode.

The portable behavioral checks used during development are documented in [`EVALS.md`](EVALS.md).

## Inspiration

Taste Loop is inspired by Anshu Chimala's [process for turning AI into a world-class designer](https://www.lennysnewsletter.com/p/how-to-turn-your-ai-into-a-world) and his open-source [Dream Loop](https://github.com/achimala/dream-loop) skill. It adapts those ideas into a user-directed product-design workflow with inspiration research, taste elicitation, interaction verification, and explicit decision checkpoints. Dream Loop's license notice is included in [`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md).

## License

MIT
