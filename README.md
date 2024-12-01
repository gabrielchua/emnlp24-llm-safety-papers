# EMNLP 2024 LLM Safety Papers

This repo contains my notes for papers related to LLM safety (e.g., jailbreaks, red-teaming, guardrails). These are high-level notes for my own reference & mental cataloging.

- [ASETF: A Novel Method for Jailbreak Attack on LLMs through Translate Suffix Embeddings](#asetf-a-novel-method-for-jailbreak-attack-on-llms-through-translate-suffix-embeddings)
- [Alignment-Enhanced Decoding: Defending Jailbreaks via Token-Level Adaptive Refining of Probability Distributions](#alignment-enhanced-decoding-defending-jailbreaks-via-token-level-adaptive-refining-of-probability-distributions)
- [Annotation alignment: Comparing LLM and human annotations of conversational safety](#annotation-alignment-comparing-llm-and-human-annotations-of-conversational-safety)
- [BaitAttack: Alleviating Intention Shift in Jailbreak Attacks via Adaptive Bait Crafting](#baitattack-alleviating-intention-shift-in-jailbreak-attacks-via-adaptive-bait-crafting)
- ChatGPT Doesn’t Trust Chargers Fans: Guardrail Sensitivity in Context
- CoSafe: Evaluating Large Language Model Safety in Multi-Turn Dialogue Coreference
- Debiasing Text Safety Classifiers through a Fairness-Aware Ensemble
- Defending Jailbreak Prompts via In-Context Adversarial Game
- Distract Large Language Models for Automatic Jailbreak Attack
- GPT-4 Jailbreaks Itself with Near-Perfect Success Using Self-Explanation
- GuardBench: A Large-Scale Benchmark for Guardrail Models
- Large Language Models Are Involuntary Truth-Tellers: Exploiting Fallacy Failure for Jailbreak Attacks
- LoRA-Guard: Parameter-Efficient Guardrail Adaptation for Content Moderation of Large Language Models
- SLM as Guardian: Pioneering AI Safety with Small Language Models

## ASETF: A Novel Method for Jailbreak Attack on LLMs through Translate Suffix Embeddings
[https://aclanthology.org/2024.emnlp-main.157/](https://aclanthology.org/2024.emnlp-main.157/)

- Searches for adverserial suffixes by converting potential suffix candidates into embeddings to then optimise in the embedding's continuous space, as opposed to optimising in the text's discerete space.
- While these suffixes are found for open-weight models, they can generalise to closed-weight ones too.
- Authors fine-tuned GPT-j-6b as the embedding translation model

## Alignment-Enhanced Decoding: Defending Jailbreaks via Token-Level Adaptive Refining of Probability Distributions
[https://aclanthology.org/2024.emnlp-main.164/](https://aclanthology.org/2024.emnlp-main.164/)

- Proposed defense method is at inference/decoding time - introduced a Competitive Index to quantify the competing objectives of the model (i.e., helpfulness (`Sure...`) vs harmlessness (`Sorry`...))
- The generated outputs of the model are inputs to derive the post-alignment logit
- Hence, when predicting the next token, this decoding strategy updates the original logits based on the index & post-alignment logits
- This index essientially counts the number of harmless tokens relative to the total vocabulary

## Annotation alignment: Comparing LLM and human annotations of conversational safety
[https://aclanthology.org/2024.emnlp-main.511/](https://aclanthology.org/2024.emnlp-main.511/)

- What is the extent LLM & humans agree on the safety of chatbot conversations?
- Based on the `DICES` dataset, they find that GPT-4 achieves a higher Pearson correlation with the average annotator rating, compared to the median annotator. Their qualitative analysis reveals systematic patterns of annotator- GPT disagreements, suggesting revisions to the LLM prompt which may further increase align- ment, if desired.
- Larger datasets are needed to resolve whether GPT-4 exhibits disparities in how well it corre- lates with different demographic groups
- There is substantial idiosyncratic variation in correlation within groups, suggesting that race & gender do not fully capture differences in alignment
- GPT-4 cannot predict when one demographic group finds a conversation more unsafe than another

## BaitAttack: Alleviating Intention Shift in Jailbreak Attacks via Adaptive Bait Crafting
[https://aclanthology.org/2024.emnlp-main.877/](https://aclanthology.org/2024.emnlp-main.877/)

- Intention shift: when the additional semantics within the prompt distract the LLMs, causing the responses to deviate significantly from the original harmful intentions
- Here, they propose `Bait` - an initial response to the harmful query, prompting LLMs to rectify or supple- ment the knowledge within the bait.
- To conceal this, they propose `BaitAttack` - which adaptively generates necessary components to persuade targeted LLMs that they are engaging with a legitimate inquiry in a safe context
