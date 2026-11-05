# FallacyLens

FallacyLens is a web application that helps readers examine English arguments for potential logical fallacies. It identifies patterns associated with 13 fallacy categories, including ad hominem, false dilemma, and faulty generalization, and explains the categories it predicts.

## What it analyzes

- **Individual arguments.** Enter an argument to see its predicted fallacy category, a confidence score, and an explanation. The app can also show additional candidate categories.
- **Debates.** Compare a premise and a rebuttal to see how closely they align and where the rebuttal may drift from the original topic.
- **Documents.** Review predictions sentence by sentence and see a heuristic integrity score for the document.

For example, an argument like “Either you support our plan or you want the company to fail” illustrates a false dilemma because it presents two choices while overlooking other possible positions.

## How it works

FallacyLens preprocesses text with NLTK and uses TF-IDF to represent it as weighted single words and two-word phrases. The training pipeline compares four classifiers on a labeled fallacy dataset: Logistic Regression, Multinomial Naive Bayes, Random Forest, and a linear Support Vector Machine. It reports accuracy, precision, recall, and F1, and selects the model with the highest test-set F1.

Flask provides the web interface and API. The interface includes analysis forms, prediction history, model performance reports, and UML diagrams. SQLAlchemy uses SQLite to store user accounts and prediction records.

## Interpreting results

The model predicts among the fallacy categories it was trained on and has no **No Fallacy** category. Use its predictions, debate alignment scores, and document integrity scores to guide a closer reading of the argument. The reported test-set F1 also reflects model selection because the same test split is used to choose the model.
