# Project Name: Media Bias Annotation (subject to change)

## Group Members: Yunlin & Issrar

1. __Background__: News coverage plays a significant role in shaping public opinion, discourse, and perception of current events. However, news media are not neutral, value-free channels; they are influenced by a range of organizational, economic, and political forces, which can introduce bias into coverage. While existing research on media bias has largely focused on the differences between media outlets, it has often overlooked the role of individual annotators, that is, the audience interpreting the news. This project seeks to fill the gap by offering new insights into how media bias is perceived by a diverse, broader public.

2. __Goals (or Research Questions)__:

- Using the “labeled_dataset” (not considering annotator characteristics), we could analyze how text-based features (e.g., word choice, sentiment, etc.) and news outlet characteristics (e.g., their political leaning and credibility) predict perceived media bias
- Using the “annotators” & “annotations” datasets: Do annotators' demographic and ideological backgrounds predict their likelihood of labeling sentences as biased?

3. __Data Source__:

- Media Bias Annotation Dataset (MBIC) - the first sample of 1,700 sentences/statements from around 1,000 news articles representing various media bias instances. The statements were reviewed by ten annotators each and contain labels for media bias identification, both on the word and sentence level. MBIC is the first available dataset about media bias reporting detailed information on annotator characteristics and their individual background.
- Citation: T. Spinde, L. Rudnitckaia, K. Sinha, F. Hamborg, B. Gipp, K. Donnay “MBIC – A Media Bias Annotation Dataset Including Annotator Characteristics”. In: Proceedings of the iConference 2021.

4. __Model features__
Annotator features: demographics (age, education level, political orientation, media consumption;
Text-based features: lexical features, bias-specific indicators (e.g., “biased_words”);
Article metadata features: news outlet credibility scores and political leaning; topic.

5. __Data Refinement__

    - Data cleaning:
        - Encoding issues: automated encoding detection and character cleaning
        - Duplicate detection and missing data handling
        - Outlier management
    - Data preprocessing:
        - Outlet reputation: convert categorical variables (e.g., “type” indicates political leaning using left/center/right; we can instead make them intervals of -1, 0, and 1);
        - Create article complexity features: controversy score, bias intensity, etc.

6. __Modeling approach__: SLR (predict perceived bias detection based on text-based features + predict inter-annotator agreement + effect of annotator characteristics on perception of bias); mixed-effect model to account for annotator-level variation.

7. __KPIs__: Model’s bias detection accuracy, false positive rate, feature interpretability, cross-topic performance consistency, inter-annotator agreement prediction.

8. __Stakeholders__: Fact-checking organizations (e.g., Politifact), social media platforms, news aggregators, news organizations, regulatory and monitoring bodies.
