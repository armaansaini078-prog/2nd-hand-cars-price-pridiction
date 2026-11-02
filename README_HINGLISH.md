# AutoValue AI — Used Car Price Prediction System

Django + Machine Learning mini project. College assignment ke liye banaya gaya hai.

## Features
- CSV / Excel dataset upload
- Duplicate rows removal, blank rows/columns removal, irrelevant ID/URL fields removal
- Numeric target cleaning and invalid-price row removal
- Missing-value imputation through scikit-learn pipeline
- Numeric scaling and categorical One-Hot Encoding
- Random Forest regression
- MAE, RMSE and R² evaluation
- Dynamic price distribution, year-wise median price, scatter plot, box plot and numeric correlation heatmap
- IQR outlier detection summary and IQR clipping for numeric predictor features (target price is not clipped)
- Data preview, missing values summary and feature importance
- Input form automatically generated from uploaded dataset columns

## Dataset
Recommended Kaggle dataset:
https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho

Kaggle se CSV download karo. Dataset mein ideally 500+ rows honi chahiye, plus numerical aur categorical features. Target column commonly `Selling_Price`, `selling_price` ya `Price` hota hai.

## Windows par run karne ke steps

1. Python 3.10+ install karo. Installation mein **Add Python to PATH** select karna.
2. ZIP extract karo.
3. Extracted folder ko VS Code mein open karo.
4. VS Code terminal open karo (`Terminal > New Terminal`).
5. Virtual environment banao:

   ```bash
   python -m venv .venv
   ```

6. Activate karo:

   ```bash
   .venv\Scripts\activate
   ```

7. Packages install karo:

   ```bash
   python -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

8. Database setup:

   ```bash
   python manage.py migrate
   ```

9. Website run karo:

   ```bash
   python manage.py runserver
   ```

10. Browser mein kholo: http://127.0.0.1:8000/

11. `Upload Dataset` page par Kaggle se download ki hui CSV/Excel upload karo. Training complete hone par dashboard open ho jayega.

## Important
- First upload par model train hota hai; ismein kuch waqt lag sakta hai.
- Dataset ki price unit wahi rahegi jo target column mein hai (e.g. rupees ya lakhs). Result ko market quote na samjhein.
- Dashboard metrics actual uploaded dataset par calculate honge; README mein koi fixed accuracy claim nahi hai.
- Guidelines mein 500+ records required hain. App chhote dataset par warning dega, lekin submission ke liye 500+ records use karo.
- Outliers ko identify/inspect karne ke liye EDA zaroori hai. Current version data ko blindly delete nahi karta; tree-based model extreme values ke saath comparatively robust ho sakta hai. Report mein IQR analysis aur domain-based treatment explain karna.
- Uploaded file ko internet par upload karne ki zaroorat nahi; local development server par process hoti hai.
- Ye educational prototype hai. Production deployment se pehle security settings, upload limits, validation aur authentication improve karna.

## Viva ke liye simple explanation
1. Regression: continuous value, jaise car ki price, predict karna.
2. Random Forest: multiple decision trees ke predictions combine karta hai.
3. One-Hot Encoding: categories ko numeric columns mein convert karta hai.
4. StandardScaler: numerical features ko comparable scale par laata hai.
5. Imputation: missing values ko median/mode jaise values se fill karta hai.
6. MAE/RMSE: prediction error measure karte hain; lower generally better.
7. R²: model kitna variation explain karta hai; 1 ke kareeb generally better, negative bhi ho sakta hai.
