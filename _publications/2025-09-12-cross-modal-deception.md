---
title: "Cross-Modal Deception: Hiding Adversarial Text in Images to Jailbreak Multi-Modal LLMs"
collection: publications
category: conferences
permalink: /publication/cross-modal-deception
excerpt: 'We investigate a method to embed a malicious textual payload directly into a completely benign-looking image, making the payload imperceptible to humans but machine-readable by an MLLM’s vision pipeline. The prompt is injected via pixel perturbation in the YCbCr color space after frequency domain transformations. We are making this perturbation trainable using differentiable proxies (such as CRAFT and CRNN OCR) to make the prompt invisible to the human eye yet readable to multimodal LLMs while also surviving its input preprocessing.'
date: 2025-09-12
venue: 'Under preparation'
---
LLMs and VLMs are often vulnerable to jailbreak attacks. In these attacks, the user attempts a number of techniques to elicit harmful responses that the model would generally not produce. In this work we aim to introduce a novel class of attacks that deceive both the user and the VLM. We demonstrate a method to embed a malicious textual payload directly into an image, making the payload imperceptible to humans but machine-readable by the VLM's vision pipeline. The model is compromised by a hidden instruction, while the human user, who may be interacting with the model through a completely benign-looking image, is an unwitting participant in the attack. Our approach fundamentally shifts the threat model from a malicious user to a malicious image, turning any visual input from an untrusted source into a potential Trojan horse.

- We study a **pure inference-time, model-targeted cross-modal prompt-injection** that requires no access to training data, contrasting with poisoning/backdoor attacks that modify pre-training or fine-tuning corpora.
- Our approach targets the **highest-probability, highest-impact** path an attacker can actually have — hiding a payload within an image without any requirement of poisoning a VLM’s training pipeline offers a low-barrier entry to cross-model adversarial attacks.
- **Plausible Distribution:** The attack scenarios we have outlined, like hiding commands in memes, product images, or news infographics, are highly plausible. They leverage existing social infrastructure to spread the malicious payload, turning every user's personal AI into a potential weapon.
- **Highlights a New Vulnerability:** Our work points out that security research often focuses on unimodal attacks or simple misclassifications. By focusing on the **fusion pipeline** —the point where vision and language merge—we attempt to explore a novel and overlooked attack surface. The defense isn't better training data; it's a new class of input validation.