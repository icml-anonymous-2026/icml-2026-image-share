Partial snippet of the response to reviewer 'AbgY'

> W3: Method-wise, maybe there can be more sophisticated settings like evolution based on feedbacks, etc. Or, maybe there can be more insights of how we can use LLMs to generate automata, e.g. the memory-augmented part is a good example.

Thank you for the suggestion. We note that improving automata generation via feedback, evolution, or iterative refinement is outside the scope of this paper, whose contribution is an LLM evaluation framework. Our goal is to isolate a model’s ability to produce a strong executable artifact in one shot, with the automaton then held fixed during evaluation. Introducing feedback-based optimization would confound this objective by measuring the outer improvement loop rather than the model’s base artifact-generation ability.

Given interest from the reviewer we include preliminary iterative-refinement experiments for a subset of models and games.

Specifically, we iteratively refine bot code from weaker models by providing reference code and strategies from stronger models. We show results in Backgammon using GPT-5.4 Nano and Gemini 3.1 Flash in Figures [1,2,3], with the “baseline” corresponding to the automata generated without iterative improvement. We repeat this experiment three times to verify consistency, and we additionally provide results for other smaller-model families in Figure [4]. We verify the same qualitative behavior in other games (Checkers [5], Lines of Action [6]). An anecdotal analysis by GPT-5.4-Codex xhigh suggests that most generated bots exhibit light conceptual borrowing from the source code with no visible carryover, while weaker Qwen models show somewhat stronger borrowing, indicating that models can incorporate strategies from stronger automata.

We also test a different refinement harness that does not provide reference automata and instead only supplies detailed match results, shown in Figure [7]. This setup is noisier, since the model must infer what to change purely from match traces. However, the results are promising where even a very small model such as GPT-5.4 Nano can reach strategies stronger than those of much larger baseline models such as Claude Opus 4.6 and GPT-5.2. We also include the corresponding result for a Qwen3 model in Figure [8].

We will include a more comprehensive version of these results as supplementary evidence, while keeping clear that they are outside the main scope and do not change the paper’s primary framing.
