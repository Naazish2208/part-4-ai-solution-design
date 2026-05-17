1. Retail AI Solution — One-Page Summary

2. Problem:

Mid-size retail businesses lose 20–35% of customers annually to churn. Current manual RFM analysis (Recency (how recently a customer bought), Frequency (how often they buy), and Monetary Value (how much they spend)) is reactive, slow, and untargeted, resulting in wasted campaign spend and missed retention opportunities.

3. AI Task Type: Sequence prediction and Recommendation

4. Required Data:
- Time-ordered transaction history (12+ months), customer profiles, campaign engagement logs, product catalogue, web/app behavioural event streams, festival tag, etc.
- Target Variable Churn label: 1 = no purchase in next 30 days, 0 = active
- Data Collection Method: POS, CRM database, web/app analytics tool, etc.
- Data quality risks: Duplicate customer records, Class imbalance (few churners vs. many actives), Seasonal bias (holiday spike skewing churn labels), etc.

5. AI Model Recommendation:

A two-stage AI pipeline built on a shared LSTM backbone:
1. Churn Prediction Engine — LSTM classifier scoring every active customer weekly with a 30-day churn probability, learning from their full transaction and engagement sequence
2. Personalised Recommendation Engine — Session-based LSTM predicting the most relevant product/offer for each at-risk customer based on recent browsing and purchase sequences

Key justification for LSTM: Customer behaviour is a time series — LSTM's gating mechanism (input, forget, output gates) is purpose-built to learn what to remember and what to discard across a customer's purchase history, making it far more appropriate than a static flat-feature model for this domain.

6. Evaluation Plan

- Technical metrics: Precision @ top 20% should be > 0.65 as marketing budget is limited; top decile quality matters, Recall (churn class)	to be > 0.70 to minimize missed at-risk customers, F1-Score to be > 0.72 for a balanced precision-recall, etc.
- Business metrics: Campaign ROI, Churn rate reduction, Average Order Value (AOV) of re-engaged customers, among others
- Human review process: Weekly model performance dashboard reviewed, quarterly full model retraining and audit, and so on

7. Risks and Mitigation Plan
- Data privacy violation: GDPR-compliant pseudonymisation + consent management
- Model drift over time: Monthly retraining + automated performance alerts
- Class imbalance (few churners): Weighted loss function + oversampling
- Cold-start (new customers <3 events): Rule-based fallback until sequence is long enough
- Over-reliance on AI: Human approval gate before all campaign sends

8. Expected Business Impact
- Customer churn rate to go down 15–25% within 6 months
- Campaign ROI to increase 30–40% vs. batch campaigns
- Revenue per retained customer	to increase 10–20% via personalisation
- Analyst time on segmentation to decrease by 80% (automated pipeline)

