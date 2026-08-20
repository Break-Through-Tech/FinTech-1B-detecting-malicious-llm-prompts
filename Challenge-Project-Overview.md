---

> ## Challenge Advisor: Update & Finalize Your Project Overview
>
> > 💡 **These grey text instructions are just for you, the team's Challenge Advisor; please delete them once you have completed the steps below.**
>
> We've pre-populated this Challenge Project Overview page — which is what will be shared with your Break Through Tech student team in August — using the details from your submission form. You should have received an email inviting you to join this repo as a Collaborator, enabling you to add files and make edits.
> 
> In order for your project to be finalized and assigned to a team, please:
> 1. **Review all sections below** and update or expand any content as needed, making sure to address the SME Feedback in the section immediately below. Look for square brackets to find the places below that require additional inputs from you (e.g., "About [Company / Org Name]").
> 2. **Add your dataset** to the [data folder](data) in this repo.
> 3. **Close the Issue assigned to you in this repo** to let us know that you have made your edits and the overview page is ready for final review. You can do this by going to the _Issues_ tab in the top left section of the menu above, add a comment that says "CA review complete", and click the button to Close the Issue. 
>
> If you're unfamiliar with how to edit a page like this in GitHub, check out [this tutorial](https://ubc-lib-geo.github.io/gis-workshop-waml-template/content/handson/edit-readme.html) for a quick overview (start with step 2 and only edit this page), and [this guide](https://ubc-lib-geo.github.io/gis-workshop-waml-template/content/markdown.html) on how to use Markdown to compose text.
>
>
> ❌ Remember that this is a public repo. Do NOT include: Proprietary data, PII, API keys, credentials, or anything confidential.

---
## 📋 BTT Internal Evaluation Notes
*(This section is for BTT staff and CAs only — remove before sharing with students)*

### Technical Vetting
| Check | Status | Notes |
| :--- | :--- | :--- |
| Python Compatibility | 🟢 | Tech stack relies on standard libraries (scikit-learn, Keras), which are fully compatible with Google Colab environments. |
| Data Readiness | 🟡 | Public datasets for prompt injection are often noisy and require significant manual cleaning and class balancing to avoid bias. |
| Resource Check | 🟢 | The project avoids heavy GPU compute or proprietary API dependencies, fitting well within free-tier Colab constraints. |

### Internal Scores
- **Student Fit Score:** 8/10
- **Technical Depth Score:** 7/10
- **Overall Recommendation:** REVISE

### Advisor Feedback Draft
This project offers a compelling, security-focused NLP application that perfectly aligns with current industry needs. To succeed in our 12-week model, I recommend focusing exclusively on a single vectorization approach (e.g., embeddings) to bypass the overhead of comparing too many feature extraction methods. Secondly, ensure students define a static 'threat landscape' early on to prevent them from chasing an infinite number of jailbreak variations. Please confirm these scoping guardrails to proceed.

---

# Detecting Malicious LLM Prompts: A Classifier for Prompt Injection and Jailbreak Attacks

**Company / Org:** Ripple  
**Challenge Advisor:** Naga Sujitha Vummaneni, nv262@cornell.edu  
**AI Studio Coach:** Om Kamath, om.kamath@breakthroughtech.org   
**Program:** Break Through Tech AI Studio - Fall 2026  

---

## 🏢 About Ripple
Ripple is a technology-forward organization dedicated to securing the next generation of generative AI applications. They focus on identifying vulnerabilities in Large Language Models to ensure enterprise systems remain resilient against adversarial manipulation.

---

## 🎯 The Challenge
### Project Summary
In this project, you will use a labeled dataset of benign and adversarial text prompts (prompt-injection and jailbreak attempts collected from public repositories) and NLP text-vectorization (TF-IDF and word embeddings) with supervised classifiers in scikit-learn and a feedforward neural network in Keras to build a model that detects and flags malicious prompts before they reach a production LLM. This will help our company address the growing security risk of LLM-powered applications being manipulated into leaking data, bypassing safety controls, or executing unintended instructions.

### Success Criteria
A working classifier evaluated with precision/recall/F1 and a confusion matrix, with explicit attention to the false-negative cost (a missed attack is worse than a false alarm), benchmarked against a baseline (e.g., logistic regression vs. the neural net), plus a short analysis of failure modes and dataset bias.

### Stretch Goals

This project has several natural stretch goals that add depth without breaking the free-Colab / no-API-key constraints:

- Multi-class attack categorization. Move beyond binary (malicious vs. benign) to classify type of attack — direct injection, role-play jailbreak, instruction-override, obfuscation/encoding-based, etc. This adds a meaningful labeling and class-imbalance challenge.
- Transformer-based embeddings. Upgrade from TF-IDF to pretrained sentence embeddings (e.g., a small Sentence-Transformers model) for feature extraction, then compare performance against the classical baseline. Runs on free Colab and teaches transfer learning intuitively.
- Adversarial robustness testing. Have the team generate simple perturbations of known attacks (synonym swaps, spacing tricks, leetspeak, base64-style encoding) and measure how much detection degrades — a hands-on lesson in why security models need adversarial evaluation.
- Explainability layer. Add token-level attribution (e.g., LIME/SHAP or attention/coefficient inspection) so the model can show why a prompt was flagged — turning a black-box classifier into something a security team could actually trust.
- Bias and fairness audit. Test whether the classifier disproportionately flags benign prompts in certain languages, dialects, or topic areas, connecting directly to the fairness/bias-mitigation skills from ML Foundations.
- Lightweight guardrail demo. As a capstone, wrap the final model in a simple input-filtering function and show it intercepting attacks in a mock prompt pipeline — a tangible, presentable artifact without needing any live LLM or API key.

These are sequenced roughly easiest-to-hardest, so a fast-moving team can keep climbing while a team that needs more time still lands a complete core deliverable.

### Project Milestones
Use these milestones to guide your work. Your team will create a GitHub Projects board to track tasks within each milestone.

| Month | Milestone | Key Activities |
|---|---|---|
| September | Threat Modeling & Data Foundation | Business understanding (threat model: what is prompt injection vs. jailbreak), data consolidation, EDA, and preprocessing/labeling reconciliation. |
| October | Feature Engineering & Baseline Models | Feature engineering (TF-IDF, embeddings), baseline classical models in scikit-learn, evaluation metric selection. |
| November | Neural Modeling & Error Analysis | Feedforward neural net in Keras, model selection across candidates, error analysis and bias/fairness review. |
| December | Final Evaluation & Delivery | Final evaluation, documentation, GitHub repo cleanup, and presentation. |

> **Note for the team:** Please create a GitHub Projects board in this repository to break these milestones into weekly tasks. Go to the **Projects** tab → **New project** → Choose **Board** → Add columns for each month.

---

## 📊 Dataset
**Name and Source:** PromptGame Dataset: Prompt Injection Attack Benchmark and Defense Evaluation Data   
**Format:** CSV, TSV, and JSON.  
**Size:** Under 1GB.  
**Location:** https://ieee-dataport.org/documents/promptgame-dataset-prompt-injection-attack-benchmark-and-defense-evaluation-data  

### Key Details
- [Brief description of what's in the data]
- [Any known limitations or preprocessing needed]
- [Link to data dictionary or documentation, if available]

---

## 🛠️ Suggested Approach

**ML Problem Type:** Classification, NLP, Deep Learning / Neural Networks, LLMs / Generative AI, Transfer Learning / Pre-trained Models  

**Recommended Libraries:**
- [e.g., pandas, scikit-learn, TensorFlow, Hugging Face]

**Evaluation Metrics:**
- [e.g., Accuracy, Precision/Recall, RMSE, BLEU score]
  
---

## 📚 Resources to Get Started

The following resources will help your team understand the problem space and potential technical approaches for this project:

**Background Reading:**
- [e.g., Link to an article or blog post about the problem domain]
- [e.g., Link to an industry report or case study]

**Technical Tutorials:**
- [e.g., Link to a free tutorial on the ML technique(s) involved]
- [e.g., Link to documentation for a key library or tool]

**Code Examples:**
- [e.g., Link to a relevant GitHub repo]
- [e.g., Link to a sample implementation or starter code]

**Other:**
- [Links to any additional resources — e.g., papers, videos, podcasts, etc.]

*Feel free to explore beyond these, and share anything interesting you find with me!*

---

## 🤝 How We'll Work Together

**Official check-ins:** During our biweekly 45-minute AI Studio Lab Section meeting block (2nd and 4th week of every month)

 **Other ways to reach out to me with questions:** 
* [e.g., Your team's channel within Break Through Tech’s Discord space]
* [e.g., Email; please copy your teammates and AI Studio Coach]
* [e.g., Request a team check-in on Zoom]
* [Note: I will aim to respond within 48 hours. Please reach out to your AI Studio Coach with urgent questions.]

> 💡 **Challenge Advisor: Please update the above based on your availability and preference. If you are not able to answer questions or meet with fellows outside of the biweekly Lab Section check-ins, simply write in "N/A (only available during the official check-in times)"**

**Recommended free coding / collaboration tools**
* […]
* […]

---

## 🚀 Getting Started

1. **Review this overview document** and note any questions for our first meeting
2. **Begin reviewing the dataset** using the link above
3. **Read the GitHub Projects documentation** [here](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects)

I’m excited to work with you!

---

## ❓ Questions?

Please bring any questions to our first meeting during the week of August 24th (Break Through Tech’s Bridge to Studio - Session C). 
