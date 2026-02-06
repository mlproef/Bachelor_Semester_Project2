# A Methodological Framework for High-Fidelity Social Simulation
Iterative Prompt Engineering for Interpretable Persuasion Analysis
## About the Project
This repository contains a research project dedicated to structuring persuasion dialogs for subsequent causal analysis.
The goal of the project is to transform unstructured dialogs from the PersuasionForGood corpus into an interpretable, utterance-level representation suitable for:
 - causal discovery,
 - analysis of persuasion mechanisms,
 - interpretable modeling of user behavior.
The project focuses not on prediction, but on understanding the causal relationships between:
 - persuasion strategies,
 - emotional responses,
 - the dynamics of interest in donating,
 - the final decision to donate.
## Used data
**Dataset**: PersuasionForGood
**Scenario**: dialogs between a persuader and a target in the context of charitable donations
**Volume**: 
  - 1,017 dialogs
  - 10,000+ utterances
  - 69.9% of conversations end with a donation.




## Pipeline Architecture
The project implements a multi-step NLP pipeline that sequentially extracts interpretable variables from dialogs:
 1) **Detection of Persuasion Strategies** Classifying persuader messages into one of the persuasion strategies → hierarchical scheme: category → strategy
 2) **Emotional Tone Classification** Determining the emotional tone of target responses → negative / neutral / positive
 3) **Willingness to Donate Estimation** Estimating the latent dynamic variable of interest in donating → not interested / neutral / interested

Structured Utterance-Level Representation Combining all annotations into a single temporal structure of the dialog.
The result is a sequence of causally interpretable states suitable for causal modeling.

## Persuasion Strategies
A hierarchy of 12 categories and 40 strategies is used. Based on classic works in social psychology (Cialdini, Kahneman, Batson, et al.).
A separate category, Conversation Management, has been introduced for: 
 - greetings,
 - maintaining the dialog,
 - organizational messages → this prevents "stretching" strategies where there is no conviction.

The classification is implemented in 2 stages:
 - **category selection**,
 - **strategy selection within the category**.



## Key Findings
Strategies → Emotional: \
Tone Fear Appeal and Guilt Induction more often evoke **negative emotions**. Reciprocity and Conversation Closing are the **most emotionally positive**. 
Strategies → Interest in Donating: \
Pressure strategies are associated with an **increase in "Not Interested."** Commitment & Consistency and Foot-in-the-door are associated with an **increase in "Interested."** 
Strategies → Donation The most effective strategies are:
- Reciprocity (80.7%)
- Unity
- Activation of Personal Commitment
The least effective:
- Guilt Induction
- Fear Appeal

## Joint Analysis (key part)
The project implements a joint analysis that combines: Strategy → Emotions → Interest → Donation.
It shows that: effective strategies form a sustainable positive chain, pressure can have a short-term effect but worsens the quality of interaction, emotional tone and interest act as mediators, not just correlates.
This lays the foundation for structural causal models (SCMs) and counterfactual analysis.


## Technologies and Tools
 - LLM (Qwen3:30B) - Interest and Emotional Tone Classification
 - Prompt Engineering - Hierarchical Strategy Classification
 - Python / Pandas / Matplotlib / Seaborn
 - Interpretable NLP, without model fine-tuning


## Practical Value
The project demonstrates: how to prepare dialog data for causal inference, how to construct interpretable intermediate variables, how to analyze not just what works, but also why.
Suitable as a foundation for: adaptive dialog systems, social simulation, explainable AI, human-centered NLP.
