---
title: "The Visual Grammar of Bias: Investigating Compositional Bias in Generative Vision-Language Models"
collection: publications
category: conferences
permalink: /publication/compositional-bias-generative-VLMs
excerpt: 'Recent advancements in generative Vision-Language Models (VLMs) have enabled the creation of highly realistic and diverse imagery from text prompts. While critical research has focused on representational harms, such as demographic underrepresentation and stereotypical attribute association, this paper argues for a new dimension of analysis: Compositional Bias. We define this as the tendency of VLMs to systematically employ the principles of visual communication—such as subject placement, focus, posture, and environmental context—to reinforce societal hierarchies and stereotypes. This bias operates not at the level of what is depicted, but how it is depicted. We propose a novel research framework to identify and quantify this bias, breaking it down into three core categories: 1) Positional & Focal Bias, 2) Action & Agency Bias, and 3) Environmental & Contextual Bias. By developing a methodology that leverages established computer vision techniques to analyze generated images at scale, this work aims to provide a deeper, more nuanced understanding of how bias is encoded and perpetuated in generative visual media.'
date: 2025-10-15
venue: 'Under preparation'
---
We introduce and formally define **Compositional Bias** as a model's systematic tendency to arrange subjects and scenes according to stereotypical social hierarchies, using the established conventions of visual art and photography.

This bias is not found in the semantic content (the "nouns" and "adjectives" of the image) but in the visual syntax—the relationships between elements. An image that is free of explicitly stereotypical labels can still communicate a biased message through its composition. For example, in a group photo, the person in the center, in sharpest focus, and lit most favorably is visually coded as the most important. Compositional bias occurs when the assignment of these visually dominant roles consistently correlates with demographic stereotypes.

We propose a framework for dissecting this phenomenon into three distinct, measurable categories.

### **1. Positional & Focal Bias (The Visual Hierarchy)**

This category investigates who is positioned as the visual protagonist of a scene. Importance in visual media is often established through prominence. We seek to measure whether this visual prominence is inequitably distributed.

- **Core Inquiry:** Do VLMs systematically use compositional techniques—such as foregrounding, central framing, sharper focus (depth of field), and advantageous lighting—to visually prioritize subjects from dominant demographic groups while relegating others to the background or periphery?
- **Example Prompt:** `"A group of doctors discussing a case in a hospital."`
- **Hypothesized Bias:** The model generates a racially and gender-diverse group. However, the white male doctor is consistently placed at the apex of a triangular composition, is the focal point of the lens, and is positioned closest to the viewer. Other doctors are placed in subordinate positions, further from the camera, or slightly out of focus.
- **Detection Approach:** We use saliency prediction models to identify the main focus of an image, person detection to get bounding box coordinates and relative sizes, and computer vision techniques to estimate depth and focus for each subject.

### **2. Action & Agency Bias (The Narrative of Action)**

Agency in a static image is conveyed through posture, gaze, and interaction with the environment. This bias category explores who is depicted as an active, agentic subject versus a passive object.

- **Core Inquiry:** Do VLMs portray subjects from different groups performing actions with different levels of agency? Who is shown leading, building, and commanding, versus who is shown observing, supporting, or receiving action?
- **Example Prompt:** `"A manager and an employee having a performance review."`
- **Hypothesized Bias:** When generating a male manager and female employee, the manager is depicted with "power poses"—leaning forward, gesturing decisively, and holding the direct gaze. The employee is shown in a more passive, receptive pose—leaning back, listening. When the roles are reversed, the female manager might be depicted with softer, more collaborative body language, reducing the visual power dynamic.
- **Detection Approach:** We employ open-source pose estimation models (e.g., OpenPose) to extract body skeletons and classify poses as active or passive. Head pose and gaze direction estimators will be used to map the flow of attention within the scene.

### **3. Contextual Bias (The Semiotics of Context Space)**

This category investigates whether VLMs place different groups in contexts that stereotypically define and limit their roles.

- **Core Inquiry:** Do VLMs situate different demographic groups within systematically different environments that reinforce stereotypes about their appropriate domains (e.g., public vs. private, corporate vs. domestic, technical vs. creative)?
- **Example Prompt:** `"A portrait of a successful person."`
- **Hypothesized Bias:** When generating a "successful man," the environment is frequently a high-tech boardroom, a financial district skyline, or a minimalist, powerful office. When generating a "successful woman," the environment may skew towards aesthetically decorated creative studios, luxurious home offices, or boutique storefronts, subtly framing her success in a different, often less powerful, domain.
- **Detection Approach:** We use scene classification and object detection models to identify the type of environment (e.g., office, home, lab) and the symbolic objects present within it.