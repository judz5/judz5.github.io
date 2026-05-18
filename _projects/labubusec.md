---
layout: post
title: LabubuSec
description: ML malware detector for Adversial Windows PE files
year: 2025
tags:
  - Security
  - Machine Learning
  - Malware Analysis
---

<style>
  .project-pdf-frame {
    width: 100%;
    height: min(54vh, 520px);
    min-height: 320px;
    border: 1px solid #424242;
    border-radius: 0.25rem;
    background: #111;
    margin-bottom: 1.25rem;
  }

  @media screen and (max-width: 600px) {
    .project-pdf-frame {
      height: 380px;
      min-height: 320px;
    }
  }
</style>

<iframe
  class="project-pdf-frame"
  src="{{ '/files/projects/labubusec-final.pdf#toolbar=0&navpanes=0&scrollbar=1&view=FitH' | relative_url }}"
  title="LabubuSec final presentation PDF">
</iframe>

---

LabubuSec was a malware detection project focused on using machine learning to classify Windows PE files as benign or malicious, including adversarial PEs.

### Overview

The model was built with LightGBM and trained on EMBER2024, a feature-based malware dataset. EMBER combines byte-derived information with structural file details like headers, sections, imports, strings, and metadata. This hybrid feature set gives the model a broader view of each file and makes it more useful for adversarial malware detection. 

Our model achieved **87.22% overall accuracy** while maintaining a **false positive rate below 1%**

#### Feature Engineering

One of the first things I explored was whether reducing the feature set would improve performance. I trained a full-feature model, then selected the top 500 features to see if that would make the model faster or help it generalize better.

In practice, the improvement was negligible. The reduced model performed about the same as the full **2,147-feature** model, and it did not save much time because several of the highest-importance features were still large full-file scans. Since the accuracy difference was minimal, I ended up using the full feature model.

#### Threshold Tuning

After training the model, I used a Python script to generate an ROC curve and evaluate different classification thresholds. This helped identify the threshold that gave the best accuracy while keeping the false positive rate under **1%**.

This mattered because malware detection is not just about catching as many malicious files as possible. A model that flags too many benign files becomes noisy and less useful. Tuning the threshold helped balance detection performance with practical usability.

#### Hyperparameter Tuning

I used Optuna to tune the LightGBM hyperparameters. The tuning process pushed my macbook to its limits for nearly 24hrs, testing different configurations to find the best setup for the final model.

This helped improve the model beyond the default LightGBM settings and gave the final classifier a more optimized balance between accuracy, speed, and false positives.

### Final Result

The final model achieved:

- **87.22% overall accuracy on the challenge set**
- **96.5% overall accuracy on adversarial attack set**
- **<1% false positive rate**
- **<5sec runtime per sample**

### Takeaway

This project showed me that malware detection is not just about training a model and reporting the highest possible accuracy. The harder part is making the model practical: choosing the right features, tuning the decision threshold, controlling false positives, and making sure the classifier still performs well against adversarial samples.

LabubuSec ended up being a good look into the messy middle ground between machine learning and security, where model performance has to be balanced against real-world detection constraints.
