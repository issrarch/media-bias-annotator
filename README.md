# Project: News Bias Detection Using Machine Learning

**Team**: Yunlin & Issrar

## Objective

Build a model that can automatically detect whether news sentences contain bias, helping readers identify potentially slanted reporting.

## What We Did

- **Data**: Analyzed 1,700 news sentences from various outlets, each reviewed by 10 people who labeled them as “biased” or “unbiased”
- Approach: Tested 5 different machine learning models (including XGBoost, Random Forest, and others) to find the best bias detector
- Features used: Word patterns, sentence length, number of biased words, news outlet reputation, and topic categories

## Key Results

- **Best Model**: XGBoost achieved 80% overall accuracy with 87% recall for bias detection
- Most important features: Specific word choices, outlet credibility scores, and sentence complexity were strongest predictors

### Detailed XGBoost Performance

- Optimization Trade-off Management: Lower threshold increases bias detection but also flags more neutral content as biased
- F1-Score: 73% (balanced measure combining precision and recall)
- False Positive Rate: 35% (incorrectly flags neutral content as biased)
- 13 Miss Rate: Still misses 13% of biased sentences

### Cross-Validation Stability

    - XGBoost: 85.6% ± 1.0% F1-score (best overall)
    - Random Forest: 84.3% ± 0.7% F1-score
    - Logistic Regression: 84.6% ± 0.7% F1-score
    - SVM: 84.5% ± 0.9% F1-score
    - KNN: 82.9% ± 1.5% F1-score

## Impact

This model can help:

- Social media platforms flag potentially biased content
- News readers make more informed decisions about sources
- Fact-checkers prioritize which articles to review
- Media organizations improve their reporting standards

## Next Steps

The model shows promise but could be improved with more diverse training data and fine-tuning for different news topics and outlets.
