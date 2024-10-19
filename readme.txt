1. Data Loading
We begin by loading two datasets: one for training the model and another for making predictions.

2. Checking for Missing Values
We check for any missing values in both datasets to ensure the data is clean before proceeding.

3. Feature and Label Separation
We separate the features (input data) from the labels (the target outcome we are predicting, in this case, whether a tumor is benign or malignant). We also remove irrelevant columns like id.

4. Splitting the Data
We split the training data into training and testing sets to evaluate the model's performance. This helps us measure how well the model generalizes to new data.

5. Feature Scaling
We standardize the features using a scaler so that all input variables have the same range. This is especially important for algorithms like logistic regression.

6. Training the Logistic Regression Model
We use logistic regression to find relationships between the features and the probability of a tumor being benign or malignant. We train the model using the scaled training data.

7. Making Predictions
We make predictions on both the testing set (to evaluate performance) and on new, unseen test data.

8. Evaluating the Model
We calculate the accuracy of the model by comparing the predicted labels with the actual labels from the test set. This gives us an idea of how well the model is performing.

9. Saving the Results
Finally, we save the predicted results for the test data into a CSV file, which can be used for further analysis or reporting.
The model learns how these features relate to the labels.
model.fit(X_train_scaled, y_train)
Make predictions
predictions = model.predict(X_test_scaled)  # predict the result of X_test
predictions1 = model.predict(X_test1_scaled)  # predict the result of X_test1
Create a DataFrame to save the predictions
predictions1_df = pd.DataFrame({
'id': test1_data['id'],  # keep the 'id' for reference
'predicted_diagnosis': predictions1  # store predictions
})
Save predictions to a CSV file
predictions1_df.to_csv('data/predictions.csv', index=False)
Calculate and print the accuracy
accuracy = accuracy_score(y_test, predictions)
print(f'Accuracy: {accuracy:.2f}')
