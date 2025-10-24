# Nvidia AI Day Sydney 2025

## Introduction

[Nvidia AI Day][nvidia ai day] took place as part of SXSW Sydney 2025, bringing together presentations on everything from sustainable AI infrastructure to industrial robotics and quantum computing. The day's talks spanned the full stack of AI development—from the hardware and power requirements of modern AI systems through to practical implementation challenges faced by companies like [Atlassian][atlassian]. What became clear throughout the presentations was [Nvidia's][nvidia] comprehensive approach to the AI ecosystem, touching nearly every layer from silicon through simulation to deployment.

- [From Idea to Reality: Amplifying Creativity With AI](#from-idea-to-reality-amplifying-creativity-with-ai)
- [Building a Sovereign, Green AI Factory for the Southern Hemisphere](#building-a-sovereign-green-ai-factory-for-the-southern-hemisphere)
- [Building (Quantum) Computing's Future](#building-quantum-computings-future)
- [Industrial Autonomy in the Era of Physical AI](#industrial-autonomy-in-the-era-of-physical-ai)
- [From Language to Physics: Next-Gen Robot Learning for the Real World](#from-language-to-physics-next-gen-robot-learning-for-the-real-world)
- [Transforming Teamwork: Atlassian's Next-Generation AI, Generative AI Agents, and the Future of Collaboration](#transforming-teamwork-atlassians-next-generation-ai-generative-ai-agents-and-the-future-of-collaboration)
- [Scaling AI Across an Enterprise - Combining Human and Token Intelligence](#scaling-ai-across-an-enterprise-combining-human-and-token-intelligence)

## From Idea to Reality: Amplifying Creativity With AI

_**Rev Lebaredian**: VP of Omniverse and Simulation Technology, NVIDIA_

_**Cameron Adams**: Chief Product Officer and co-founder, Canva_

In his section of the keynote address, Nvidia's VP of Omniverse and Simulation Tech Rev Lebaredian presented a conceptual reframing of AI infrastructure. Rather than "data centers" dedicated to the storage and retrieval of data, he described modern AI facilities as "intelligence factories" — taking electricity as input and producing intelligence as output in the form of tokens. Australia's natural advantages in renewable power generation and vast available space combined with a skilled workforce and stable government positions us perfectly to take advantage of this shift.

Lebaredian also made the interesting philosophical point that rather than simply providing better tools to humans, we're now adding new "participants" to teams, enterprises, and economies. In knowledge work, these take the form of AI agents. In physical work, they're robots. The focus in both instances is on tasks that are too boring, too dirty, or too dangerous for humans. In the latter case, these systems can be tested pre-deployment in Omniverse, Nvidia's digital twin platform. This provides a sandbox environment for validating AI and robotics systems before they interact with the physical world — a sensible approach to risk mitigation.

[Canva][canva] co-founder and Chief Product Officer Cameron Adams followed with themes familiar to us at Canva/[Leonardo.Ai][leonardo] around the democratisation of creativity. Leo Flow State even got a moment on the big screen. In the final Q&A with Lebaredian, Adams made some interesting comments about the sheer cost of content generation at Canva-scale and the notion that in a world of "AI Slop", humans will always value quality over quantity.

## Scaling AI Across an Enterprise - Combining Human and Token Intelligence

_**Brendan Hopper**: CIO for Technology, Commonwealth Bank of Australia_

This talk from the [Commonwealth Bank of Australia][cba] presented a framework for understanding compute evolution through three "planes": Integer (the von Neumann and Turing era with punch cards and tape), Float (beginning with the Intel 8087 and leading to tensors, transformers, and LLMs), and Quantum. The key insight is that these represent different tools for different jobs. Importantly, AI provides intelligence but not human intelligence - a distinction that matters when evaluating which problems are appropriate for AI solutions.

The "tools vs. loops" framework was particularly useful for thinking about AI deployment. Traditional software is deterministic, expensive to build but cheap to run. Moving up the stack you encounter predictive models, specialized generative models, and large general models. One emerging pattern is using large general models to generate traditional software. Another is "transactive memory" - rather than knowing everything, you maintain references to other agents or humans who have that knowledge. This scales from individual AI interactions through to company-wide and cross-economy applications.

Protocol development is evolving to match. We have MCP (Model Context Protocol) and A2A (Agent-to-Agent), but now need H2A (Human-to-Agent) and A2H (Agent-to-Human) protocols as well. Moving from agents to swarms is fundamentally about queue management - coordinating multiple AI entities. The talk concluded with an interesting observation: while [Moore's law][moores law] may be slowing, [Jevons's paradox][jevons paradox] will hold true for AI. As compute becomes more efficient, we'll use more of it rather than less. Efficiency unlocks demand rather than satisfying it.

## Building a Sovereign, Green AI Factory for the Southern Hemisphere

_**Tim Rosenfield**: Co-CEO, Firmus Technologies_

[Firmus AI][firmus] presented their vision for sustainable AI infrastructure in Australia, with a focus on environmental impact. Their "green AI" approach delivers some impressive efficiency gains: up to 50% less construction cost, 99% less water usage through chillerless computing, and 50% less land requirements. The specs are designed to accommodate the megawatt-scale GPUs coming in the near future, which is a sensible bit of future-proofing.

The centerpiece is [Project Southgate][project southgate], beginning in Tasmania and expanding to Melbourne. Georgetown is slated for a 500MW facility with 100,000 GPUs, while Wesley Vale will host a 200MW installation. The Melbourne deployment is scheduled for Q1 2026 with 18,500 GB300 GPUs. Firmus is partnering with Nvidia and CDC to bring DGX Cloud to the region, with Singapore Melbourne as the first location. The broader vision touches on Australia's potential advantages in AI infrastructure: onshore GPU assets, competitive token costs, job creation, support for renewable energy development, and retaining value within the Australian economy and tax system.

## Building (Quantum) Computing's Future

_**Prof. Jeremy O'Brien**: CEO and Co-founder, PsiQuantum_

[PsiQuantum's][psiquantum] presentation addressed the current limitations of quantum computing head-on. While there are problems that classical computers - even when augmented with AI - cannot solve, existing quantum computers face significant constraints: they're too small (hundreds of qubits) and too noisy (errors occur after only a few hundred operations).

PsiQuantum's approach centers on photonics, using light-based systems rather than traditional approaches. Their goal is to build quantum computers with millions of error-corrected qubits. This requires solving numerous challenges at scale: high-performance silicon photonics, efficient coupling between photonic chips and fiber optics, tier-1 semiconductor manufacturing capabilities, and sophisticated switching systems. The cooling requirements are particularly demanding - photons must be detected by thermal detectors operating at extremely low temperatures.

The potential applications include highly accurate simulation of chemistry (essentially lab-accurate digital experiments) that could generate high-precision, reliable data for machine learning systems. PsiQuantum is building their cryo plant near Brisbane Airport, leveraging Australia's strong history in quantum research.

## Industrial Autonomy in the Era of Physical AI

_**Rev Lebaredian**: VP of Omniverse and Simulation Technology, NVIDIA_

The industrial autonomy talk highlighted a surprising gap: in millions of factories worldwide, there's remarkably little evidence of computing technology. The bottleneck hasn't been hardware - we've been able to build capable robot bodies for years. The problem has been software. Previous generation robots required painstaking programming by specialists for highly specific, repetitive tasks, and lacked vision capabilities to adapt to changing conditions.

The shift is being driven by several factors: labor shortages (particularly for dull, dirty, and dangerous work), reshoring of manufacturing, and advances in "Physical AI". This approach treats sensor signals (image tokens, text tokens, audio tokens) as inputs and actuator signals (servo motors, etc.) as outputs. Nvidia's three-computer stack addresses the full development lifecycle: simulate with DGX (creating synthetic training data and evaluating models safely), train with Jetson AGX, and deploy with Omniverse and Cosmos. This connects back to the digital twin concept from Lebaredian's talk.

The [Isaac platform][isaac platform] is Nvidia's open robotics development offering, including foundation models, Isaac Sim for robot simulation and testing, the Newton physics engine, and Cosmos. Cosmos itself comprises three components: Cosmos Predict (a diffusion model for world generation), Cosmos Transfer (photorealistic world generation), and Cosmos Reason (a vision-language model with world understanding). Interestingly, with sensors and actuators, a room, building, or even city can be considered a robot in this framework.

## From Language to Physics: Next-Gen Robot Learning for the Real World

_**Nikko Suenderhauf**: Professor, QUT Centre for Robotics_

This session covered the evolution of robot learning approaches. While reinforcement learning has seen limited success in robotics, imitation learning and behavior cloning are showing more promise. The approach is straightforward: humans demonstrate tasks and robots learn by observing. The underlying mechanism uses generative AI - specifically diffusion models that generate robot actions rather than images.

Three key innovations were discussed. First, "Affordance Frame Detection" moves beyond pixel-level understanding to reason about tasks in terms of affordances. Rather than just identifying objects, the system understands spatial relationships (e.g., the robot's hand position relative to a teapot). The trade-off is a more sophisticated perception pipeline, but this enables both object and spatial generalization - the robot can handle variations in shape, color, and position. See [affordance-policy.github.io][affordance policy] for more details.

Second, [Physically Embodied Gaussian Splatting][pegs] uses particles to represent both the appearance and physics of objects, derived purely from vision without requiring CAD models. This creates a "simulatable" representation useful in two ways: predicting outcomes of robot actions (up to approximately 5 seconds) and serving as a simulation environment where actions can be tested before real-world deployment.

Third, LLMs are proving effective as generic planners when properly grounded in the robot's environment. The solution is hierarchical: rather than feeding the entire environment as JSON (which doesn't scale and causes attention issues), expose only the top level initially (e.g., "which room?" → "kitchen"), then drill down through the hierarchy (e.g., "which furniture?" → "cupboard"). This prevents hallucinations and maintains focus. [Sydekick Robotics][sydekick] is commercializing these approaches.

## Transforming Teamwork: Atlassian's Next-Generation AI, Generative AI Agents, and the Future of Collaboration

_**Matthew Burton**: Senior Machine Learning Engineer, Atlassian_

The Atlassian team's presentation on building their [Rovo][rovo] agent platform offered a refreshingly pragmatic take on AI orchestration. Their core philosophy: you probably don't need a complex orchestration framework. At its heart, an agent is simply an LLM in a loop calling tools. Complexity is the enemy of reliability, particularly when deploying to production.

The technical details were instructive. Their search implementation uses query rewriting to fit queries to the index (transforming "CTO" to "Atlassian CTO", or "Who is the CTO of Atlassian" to "CTO Atlassian"). For optimization they're running quantized Llama 3-8b on Triton inference server with TensorRT. Document recall relies on careful chunking strategies - sequential data in chunks with overlap, favoring markdown formatting. Re-ranking uses a cross-encoder that takes both query and passage to return a semantic relevance score.

Interestingly, fine-tuning didn't work as well as RAG (Retrieval-Augmented Generation) for their use case. The entire Atlassian REST API is exposed as tools within Rovo, demonstrating that sometimes the most powerful capability is simply providing clean access to existing functionality.

## Conclusion

Nvidia AI Day 2025 showcased the breadth of Nvidia's AI ecosystem. From Firmus AI's green data centers in Tasmania to PsiQuantum's photonics research in Brisbane, from Atlassian's pragmatic agent deployment to cutting-edge robotics research, Nvidia's technology stack was present throughout. DGX systems train the models, Jetson boards deploy them, Omniverse provides simulation and digital twin capabilities, and Isaac enables robotics development. Even the quantum computing presentations involved Nvidia partnerships.

What's notable isn't just the technical capabilities but the ecosystem strategy. Nvidia has moved well beyond selling GPUs (though that remains a core business) to defining the entire stack from silicon through simulation to deployment. The breadth of integration presented suggests this approach is working. The sustainability focus addresses real concerns about AI infrastructure's environmental impact. The emphasis on practical deployment (particularly Atlassian's philosophy of simplicity over complexity) suggests the industry is maturing beyond pure hype.

As Australia positions itself as a potential hub for AI infrastructure - leveraging onshore compute, renewable energy, and its existing technology ecosystem - Nvidia continues to dominate AI compute at every level. Based on the presentations at AI Day, they show no signs of slowing down. The company's continued innovation across the full AI stack, from power-efficient data centers through to robotic foundation models, positions them well for the next phase of AI development.

[nvidia ai day]:https://www.nvidia.com/en-au/ai-days/session-catalog/?tab.day=20251016#/
[nvidia]:https://www.nvidia.com
[atlassian]:https://www.atlassian.com
[canva]:https://www.canva.com
[leonardo]:https://leonardo.ai
[cba]:https://www.commbank.com.au
[firmus]:https://firmus.com.au
[psiquantum]:https://psiquantum.com
[isaac platform]:https://developer.nvidia.com/isaac
[affordance policy]:https://affordance-policy.github.io
[sydekick]:https://sydekick.ai
[moores law]:https://en.wikipedia.org/wiki/Moore%27s_law
[jevons paradox]:https://en.wikipedia.org/wiki/Jevons_paradox
[project southgate]:https://firmus.com.au/project-southgate
[pegs]:https://embodied-gaussians.github.io
[rovo]:https://www.atlassian.com/software/rovo
