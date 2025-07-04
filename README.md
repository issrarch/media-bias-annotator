# **Goal #1: Predicting news bias at the sentence level**

- Given a news statement/sentence, our model will predict whether it’s biased or non-biased based on textual features and news article metadata

- Modeling approach: classification (logistic regression, naive Bayes, SVM, KNN), ensemble learning (random forest & XG boost)

	- Logistic regression: great for binary classification problems, easy to interpret, can handle both text and metadata, assumes a linear relationship
	- Naive Bayes: works well with text data (tf-idf or bag of words), does not directly handle metadata
	- SVM (linear SVC): suitable for text data, effective in NLP settings
	- KNN: non-parametric, very versatile, but prone to overfitting
	- Random forest: handles high-dimensional data and captures non-linear relationships, provides feature importance
	- XG Boost: similar to rf, but requires more tuning and is less interpretable

- Workflow

	1. Text cleaning & preprocessing: remove stopwords & punctuation, tokenization, lemmatization

	2. Feature engineering: 

		- Number of biased words
		- Basic text features, including the # of words in each sentence, average word length, and unique word count
		- TF-IDF vectorization
		- Metadata: one-hot encoding for categorical variables (“outlet”, “topic”, “type”)

	3. Model training:

		- For each classifier (Logistic Regression, SVM, KNN, Random Forest, XGBoost), a separate pipeline is built combining preprocessing and the estimator
		- Each model is trained on the training set

	4. Model evaluation:

		- 5-fold stratified cross-validation is used for model comparison
		- Metrics computed: accuracy and F1-score
		- Test set performance: after model selection (based on cross-validation results), the best-performing model is evaluated on the test set, and a classification report (precision, recall, f1, support) is generated.
		- Adjust the threshold to prioritize recall for biased label


# **Goal #2: Misinformation risk**

- The question we try to answer in this phase is: can we predict the vulnerability of people to misinformation based on their media consumption habits? 

- Our model assigns a vulnerability category (Low, Medium, High, Very High) that could be used in a real-life context to design targeted positive interventions to tackle the issue of misinformation vulnerability. 

- It has a potential real-life application as a tool to predict news engagement patterns and information consumption preferences to enable media literacy interventions and evidence-based civic education programs, for example. 

1. Modeling approach: linear regression, and ensemble learning (random forest and gradient boosting) 

	- Linear regression: provides interpretable baseline performance; assumes linear relationship between features and vulnerability; random forest: modest non-linear patterns; gradient boosting: complex patterns benefit from boosting

2. Workflow

	- Notebook 1: 

		- Loaded data and did initial exploration
		- Replaced ‘media_id’ suffixes in the names 150 columns with their corresponding ‘media_name’ for better legibility
		- Selected a list of 27 variables that had theoretical links with my research question
		- Converted the survey weight category format from European comma to standard dot format
		- Handled missing values, dropped column with zero variation, saved cleaned dataset and saved a copy of the survey weight column to keep handy for later population-level analysis

	- Notebook 2:

		- Create target variable: composite `vulnerability_score`, composed of 5 weighted components (political disengagement, news disengagement, news avoidance, news fatigue, and education vulnerability)
		- Provide research sources to explain the rationale behind the variable creation strategy
		- Separate predictive variables (demographics, use frequency, main news source choice, media channel usage) and variables used to create the target variable (interest in politics (*not* about political interest), interest in news, news avoidance, news worn out, education). I isolated the `political_orientation` variable to prevent data leakage (too similar to political interest and might bias the model). Validated separation.
		- Simple transformation of some variables (not touching outcome variables to avoid data leakage): created feature-only dataset, encoded categorical variables, ordinal encoding for ordered categories, one-hot for nominal categories, age groups for numeric age variable, media usage count variables. Created final dataset. No missing values.

	- Notebook 3: 

		- Stratified train/validation/test split (70/15/15)
		- Separated features and target variable
		- Split validation. Save splits.

- Notebook 4:

	- Model training
	- Feature scaling for linear model and fit only on training data
	- Model selection:
		- Linear regression: simple baseline, interpretable coefficients
		- Random forest: handles non-linearity, feature importance
		- Gradient boosting: handles complex patterns
	- Define models and their parameters
	- Model training and model comparison
		- Best model: gradient boosting	
	- Model performance visualization
	- Feature importance analysis and visualization
	- Final model evaluation on test set
		- Good consistency
	- Model saving with metadata using joblib

- Notebook 5: 

	- Exploration of business applications of the model
	- Business risk segmentation analysis

		- Medium risk: prevention programs
		- Low risk: maintenance 
		- High and Very High: immediate intervention

	- Feature importance for business

		- Media diversity drives vulnerability to misinformation; news consumption frequency increases vulnerability; age affects susceptibility patterns

	- Business insights: prioritize targeting media diversity and promote traditional media consumption
    
	- To see this portion of the work: [Misinformation Risk  Repository](https://github.com/issrarch/misinformation-risk)
