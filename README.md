# GenUIgood

**A curated guide to generative UI: interfaces that AI composes for a specific person, at a specific moment.**

Instead of sending everyone through the same predefined screens, a generative UI system decides what to show based on the request and what it already knows about the user. It then draws that screen from real, interactive components. This list collects the protocols, frameworks, research and writing behind it.

Contributions welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Contents

- [The three patterns](#the-three-patterns)
- [Protocols and specs](#protocols-and-specs)
- [Frameworks and SDKs](#frameworks-and-sdks)
- [Where generative UI runs today](#where-generative-ui-runs-today)
- [Design and prototyping tools](#design-and-prototyping-tools)
- [Research papers](#research-papers)
- [Essays and articles](#essays-and-articles)
- [Examples and starters](#examples-and-starters)
- [Design principles](#design-principles)
- [Related lists](#related-lists)

## The three patterns

Most projects fall into one of three approaches. The difference is how much freedom the model gets.

| Pattern | How it works | Trade-off | Examples |
|---|---|---|---|
| **Controlled** | Developers build the components. The model picks which ones to show and fills in their props. | Most reliable and on-brand, but limited to what you've built. | Vercel AI SDK, Tambo, CopilotKit, Hashbrown |
| **Declarative** | The model writes a UI description (usually JSON). The client draws it with its own native components. | Safe across web and mobile, and the spec can be saved and redrawn later. | A2UI, json-render, OpenUI, Adaptive Cards |
| **Open-ended** | The model writes HTML or code, which runs in a sandbox. | Most flexible, but hardest to keep consistent and secure. | MCP Apps, OpenAI Apps SDK, Claude Artifacts |

## Protocols and specs

How an agent describes an interface to the app that displays it.

- [A2UI](https://github.com/google/A2UI) – Google's open protocol for agent-generated UI. Agents send a declarative JSON description and the host app draws it with its own trusted components on web, Flutter or mobile.
- [MCP Apps](https://github.com/modelcontextprotocol/ext-apps) – The first official extension to the Model Context Protocol. MCP tools can return interactive UI that runs in a sandboxed iframe inside the host.
- [MCP-UI](https://github.com/MCP-UI-Org/mcp-ui) – The community SDK that pioneered UI resources over MCP and fed into MCP Apps.
- [AG-UI](https://github.com/ag-ui-protocol/ag-ui) – An event-based protocol that streams agent state, messages and tool calls to a frontend. Other generative UI specs often build on it.
- [OpenUI](https://github.com/thesysdev/openui) – Thesys's open standard for generative UI, built around a compact format designed to use fewer tokens than JSON.
- [Adaptive Cards](https://github.com/microsoft/AdaptiveCards) – Microsoft's long-standing JSON card format, used by Teams and Copilot to render structured, interactive responses.

## Frameworks and SDKs

Libraries for building generative UI into your own product.

- [Vercel AI SDK](https://github.com/vercel/ai) – A TypeScript toolkit where tool calls map to React components ([docs](https://ai-sdk.dev/docs/ai-sdk-ui)).
- [Tambo](https://github.com/tambo-ai/tambo) – A React SDK. You register components with typed schemas, and the agent chooses and fills them in. Components can stay on screen and update over time.
- [json-render](https://github.com/vercel-labs/json-render) – Vercel Labs' framework where the model can only compose layouts from a catalog of components you define.
- [CopilotKit](https://github.com/CopilotKit/CopilotKit) – Chat components and frontend tools that render UI inside the conversation, built on AG-UI.
- [Hashbrown](https://github.com/liveloveapp/hashbrown) – Generative UI for React and Angular, where the model renders components you expose to it.
- [Crayon](https://github.com/thesysdev/crayon) – Thesys's React component library for rendering generative UI responses, paired with the [C1 API](https://docs.thesys.dev/guides).
- [assistant-ui](https://github.com/assistant-ui/assistant-ui) – React primitives for AI chat, with support for rendering tool calls as UI.
- [LangGraph generative UI](https://docs.langchain.com/langsmith/generative-ui-react) – Lets LangGraph agents push React components to the client.
- [LlamaIndex chat-ui](https://github.com/run-llama/chat-ui) – Chat components for LLM apps, including custom widgets in responses.

## Where generative UI runs today

Consumer products where people already use generated interfaces.

- [OpenAI Apps SDK](https://github.com/openai/openai-apps-sdk-examples) – Apps that render interactive UI inside ChatGPT, built on MCP.
- Claude Artifacts – Interactive pages and tools that Claude builds and that people can keep and share.
- [Gemini dynamic view](https://research.google/blog/generative-ui-a-rich-custom-visual-interactive-user-experience-for-any-prompt/) – Google's generative UI experiments that build a custom interactive page for each prompt.
- Microsoft Copilot – Uses Adaptive Cards to render structured responses.

## Design and prototyping tools

Tools that generate UI for people building products. These are a neighbour of runtime generative UI and not the same thing.

- [v0](https://v0.dev) – Vercel's tool for generating React and Tailwind interfaces from prompts.
- [Google Stitch](https://stitch.withgoogle.com) – Google Labs' design canvas that turns prompts into UI designs and frontend code.
- [wandb/openui](https://github.com/wandb/openui) – An open-source tool for describing a UI and seeing it rendered live.
- [tldraw make-real](https://github.com/tldraw/make-real) – Draw a wireframe and turn it into a working HTML prototype.

## Research papers

- [Generative UI: A rich, custom, visual interactive user experience for any prompt](https://research.google/blog/generative-ui-a-rich-custom-visual-interactive-user-experience-for-any-prompt/) – Google Research, 2025. Shows that current models can build full custom interfaces per prompt, and that people often prefer them to plain text answers.
- [Generative Interfaces for Language Models](https://arxiv.org/abs/2508.19227) – 2025. Proposes having models create interactive interfaces in place of chat replies, and evaluates when users prefer them.
- [DynaVis: Dynamically Synthesized UI Widgets for Visualization Editing](https://arxiv.org/abs/2401.10880) – Microsoft Research, CHI 2024. Generates small purpose-built widgets on the fly for each editing task.
- [Biscuit: Scaffolding LLM-Generated Code with Ephemeral UIs in Computational Notebooks](https://arxiv.org/abs/2404.07387) – 2024. Adds temporary UIs between the user and generated code so people can steer it.
- [UICoder: Finetuning Large Language Models to Generate User Interface Code through Automated Feedback](https://arxiv.org/abs/2406.07739) – Apple, NAACL 2024. Trains models to write UI code that compiles and matches its description.

## Essays and articles

- [Malleable software](https://www.inkandswitch.com/essay/malleable-software/) – Ink & Switch, 2025. Makes the case for software that people can reshape to fit their own needs.
- [GenUI vs. Vibe Coding: Who's Designing?](https://www.nngroup.com/articles/genui-vs-vibe/) – Nielsen Norman Group.
- [The Most Exciting Development in GenUI: Buttons and Checkboxes](https://www.nngroup.com/articles/genui-buttons-and-checkboxes/) – Nielsen Norman Group.
- [Outcome-Oriented Design: The Era of AI Design](https://www.nngroup.com/videos/the-era-of-ai-design/) – Nielsen Norman Group (video).
- [Generating code for generative UI is a bad idea](https://www.thesys.dev/blogs/generating-code-for-generative-ui-is-a-bad-idea) – Thesys. Argues for specs over raw generated code.
- [The landscape of generative UI in 2026](https://dev.to/blove/the-landscape-of-generative-ui-in-2026-ad6) – A survey of how major products ship generative UI.
- [Generative UI in 2026: what actually works for developers](https://alexcloudstar.com/blog/generative-ui-developer-guide-2026/)
- [Google A2UI explained](https://www.analyticsvidhya.com/blog/2025/12/google-a2ui-explained/) – An introduction to how A2UI works.
- [MCP Apps: the spec that turns MCP servers into UI platforms](https://www.morphllm.com/mcp-apps)
- [AG-UI on the Thoughtworks Technology Radar](https://www.thoughtworks.com/radar/platforms/ag-ui-protocol)

## Examples and starters

- [vercel-labs/ai-sdk-preview-rsc-genui](https://github.com/vercel-labs/ai-sdk-preview-rsc-genui) – Vercel's original generative UI demo.
- [langchain-ai/langgraphjs-gen-ui-examples](https://github.com/langchain-ai/langgraphjs-gen-ui-examples) – LangGraph agents that render React UI.
- [openai/openai-apps-sdk-examples](https://github.com/openai/openai-apps-sdk-examples) – Example apps for ChatGPT.

## Design principles

What we've learned building generative UI for a product. These are opinions, not standards.

1. **Show one thing at a time.** A generated screen should have one clear answer, then supporting detail. Build it in order so the eye has one place to go.
2. **Let the model choose and let the system compute.** The model decides which components to show. Numbers, prices and rules come from deterministic code.
3. **Context makes it personal.** The interface is only as good as what the system knows about the person. Show which facts it used so they can be checked.
4. **Prefer real components to generated pixels.** Components from your own design system keep the result on-brand, accessible and testable.
5. **Let people keep what was built.** If a generated view is useful, let the user save it and come back to it with fresh data.

## Related lists

- [narrowin/awesome-generative-ui](https://github.com/narrowin/awesome-generative-ui)
- [rapidpages/awesome-gen-ui](https://github.com/rapidpages/awesome-gen-ui)

## License

[CC0 1.0](LICENSE). To the extent possible under law, the contributors have waived all copyright to this list.
