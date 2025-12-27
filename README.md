# Healthcare Insurance Cost Prediction

A professional machine learning application that predicts healthcare insurance costs with a modern Streamlit dashboard, user authentication, and advanced scenario analysis.

## � Live Application

**Visit the deployed app**: https://predicting-healthcare-insurance-cost.streamlit.app/

## �📊 Project Overview

This project provides a **full-stack insurance cost prediction system** with:

### Input Features
- **Age**: Customer age (18-64 years)
- **Sex**: Customer gender (male/female)
- **BMI**: Body Mass Index (15-55)
- **Children**: Number of dependents (0-5)
- **Smoker Status**: Smoking status (yes/no)
- **Region**: Geographic region (northwest, northeast, southwest, southeast)

### Key Features

✅ **Professional Streamlit Dashboard** with dark theme and responsive design  
✅ **User Authentication** with SQLite database (login/signup)  
✅ **4-Tab Interface**:
   - **Predictor**: Real-time cost estimation with detailed breakdown
   - **Scenarios**: What-if calculator (quit smoking, lose weight, change region, age projection)
   - **Insights**: Model information, cost factor explanations, improvement strategies
   - **History**: User prediction history with statistics (latest, highest, lowest, average costs)

✅ **Gradient Boosting Model** (R² = 0.8383, best performer)  
✅ **Advanced ML Models** (Linear, Ridge, Lasso, Random Forest, Gradient Boosting)  
✅ **Comprehensive Analysis** in Jupyter notebook with full EDA and visualizations  

## 🎯 Model Performance

| Model | RMSE | MAE | R² Score |
|-------|------|-----|----------|
| Gradient Boosting | $4,678.79 | $2,721.41 | **0.8383** |
| Random Forest | $4,910.03 | $2,854.83 | 0.8219 |
| Linear Regression | $6,329.83 | $4,395.49 | 0.7040 |

### Feature Importance (Gradient Boosting)
1. **Smoker Status**: 68.8% ⚠️ Dominant cost driver
2. **BMI**: 17.8%
3. **Age**: 11.9%
4. **Children**: 1.0%
5. **Region**: 0.3%
6. **Sex**: 0.1%

**Key Insight**: Smoking status is the single most influential factor, accounting for ~69% of cost variance. Non-smokers can save 85%+ on premiums.

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/Lerato-leo/Predicting-Healthcare-insurance-cost
cd Predicting-Healthcare-insurance-cost
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Streamlit App
```bash
streamlit run streamlit_app.py
```

The app will open at **http://localhost:8501**

### 4. Access the Application

Navigate to http://localhost:8501 in your browser:

1. **Landing Page**: Overview of the application
2. **Sign Up / Login**: Create account or log in
3. **Dashboard** (4 Tabs):
   - **Predictor**: Enter demographics and get instant insurance cost estimate
   - **Scenarios**: Explore what-if scenarios (quit smoking, lose weight, change region, future age projection)
   - **Insights**: Learn about cost factors and improvement strategies
   - **History**: View your prediction history and statistics

## 📓 Jupyter Notebook Analysis

Open `The project.ipynb` to see complete analysis:
- ✅ Data cleaning and preprocessing (removed negative values, standardized encoding, handled missing data)
- ✅ Exploratory Data Analysis (EDA) with visualizations
- ✅ Feature correlations and relationships
- ✅ Model training and evaluation (5 different algorithms)
- ✅ Residual analysis
- ✅ Feature importance analysis

```bash
jupyter notebook "The project.ipynb"
```

## 🔐 User Authentication

- **Database**: SQLite (users.db)
- **Password Security**: SHA256 hashing
- **Session Management**: Streamlit session state
- **Features**:
  - User signup with validation
  - Secure login
  - Per-user prediction history
  - User profile management

## 📁 Project Structure

```
Predicting-Healthcare-insurance-cost/
├── streamlit_app.py               # Main Streamlit web application
├── The project.ipynb              # Jupyter notebook with full analysis & training
├── requirements.txt               # Python dependencies
├── README.md                      # This file
├── insurance.csv                  # Training data (1,338 samples)
├── validation_dataset.csv         # Validation data
├── model.pkl                      # Trained Gradient Boosting model
├── scaler.pkl                     # Feature StandardScaler
└── users.db                       # SQLite user database
```

## 🔍 Key Insights

### Smoking Impact Analysis
- **Smoker Cost Impact**: 68.8% of prediction variance
- **Realistic Comparison**:
  - Non-smoker (26F, BMI 25, no kids): ~$1,614/year
  - Smoker (26F, BMI 25, no kids): ~$14,168/year
  - **Savings if quit**: ~$12,554/year (88.6% reduction)
  
This reflects real-world insurance pricing where smoking is the single most important cost driver.

### Data Quality
- **Training Data**: 1,207 clean records after preprocessing
- **Cleaning Applied**: 
  - ✅ Removed negative ages
  - ✅ Standardized categorical encoding
  - ✅ Handled missing values
  - ✅ Corrected outliers

## 📊 Model Performance Summary

**Best Model**: Gradient Boosting
- **R² Score**: 0.8383 (explains 83.83% of variance)
- **RMSE**: $4,678.79
- **MAE**: $2,721.41

**Other Models Tested**:
- Random Forest: R² 0.8219
- Linear Regression: R² 0.7040
- Ridge Regression: R² 0.7050
- Lasso Regression: R² 0.7055

## 🛠️ Development

### Environment Setup
```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Running the Application
```bash
# Start Streamlit app
streamlit run streamlit_app.py
```

### Viewing the Analysis
```bash
# Open Jupyter notebook for full analysis
jupyter notebook "The project.ipynb"
```

## 📝 Data Preprocessing

The notebook includes complete data preprocessing:
1. **Type Conversion**: Charges from string to float
2. **Standardization**: Region values (lowercase), Sex values (consistent)
3. **Missing Data**: Removed rows with missing values
4. **Data Validation**: Fixed negative ages and children values
5. **Encoding**: Converted categorical variables for modeling

## 🚀 Usage Scenarios

### Predict Your Cost
1. Launch the app and create an account
2. Enter your demographics
3. Get instant cost estimate with breakdown
4. Understand cost drivers

### Explore What-If Scenarios
1. Find estimated cost reduction if you quit smoking
2. Calculate savings by losing weight
3. Compare costs across different regions
4. Project costs at future age

### Track Your History
1. View all your previous predictions
2. Monitor cost changes over time
3. See your lowest and highest quoted costs
4. Understand trends in your predictions

## 📚 Technical Stack

- **Frontend**: Streamlit 1.28.0
- **Backend**: Python 3.11
- **ML Framework**: Scikit-learn 1.3.0
- **Deep Learning**: TensorFlow 2.15.0
- **Database**: SQLite3
- **Data Processing**: Pandas 2.0.3, NumPy 1.24.3

## 🐛 Troubleshooting

### Streamlit app won't start
```bash
# Make sure you're in the project directory
cd Predicting-Healthcare-insurance-cost

# Reinstall Streamlit
pip install --upgrade streamlit

# Run with explicit Python path
python -m streamlit run streamlit_app.py
```

### Model files missing
The `model.pkl` and `scaler.pkl` are pre-trained and included. If missing, the notebook (`The project.ipynb`) contains code to retrain them.

### Port 8501 already in use
```bash
streamlit run streamlit_app.py --server.port=8502
```

## 📄 License

MIT License - Open source and free to use

## 👤 Author

**Lerato-leo** - GitHub: [@Lerato-leo](https://github.com/Lerato-leo)

## 🙋 Support & Questions

For issues or questions:
1. Check the README and notebook thoroughly
2. Review GitHub issues
3. Create a detailed issue report with:
   - Error message/screenshot
   - Steps to reproduce
   - Your Python/Streamlit version

---

**Last Updated**: December 27, 2025  
**Version**: 2.0 - Production Ready  
**Status**: ✅ Complete and Fully Functional

## 🎉 Project Status

### ✅ Completed Milestones
- [x] TensorFlow ML model integration
- [x] Multiple ML algorithms comparison (5 models)
- [x] Gradient Boosting selected (R² 0.8383)
- [x] Professional Streamlit dashboard
- [x] Dark theme with purple accents
- [x] User authentication system
- [x] Prediction history tracking
- [x] What-if scenario calculator
- [x] 4-tab responsive interface
- [x] Data quality validation
- [x] Complete Jupyter notebook analysis
- [x] Model deployment ready
- [x] All code errors resolved
- [x] Configuration optimized
- [x] Documentation complete

### 🚀 Ready for Deployment
The application is fully functional and ready for:
- Local use with authentication
- Docker containerization
- Cloud deployment (AWS, Azure, Google Cloud)
- Integration into larger systems

## 📞 Contact & Support

For questions or issues:
- Review the comprehensive README and Jupyter notebook
- Check GitHub issues
- Run the application and explore all features

---
## 🎯 Future Improvements

- [ ] Add model interpretability (SHAP values)
- [ ] Implement cross-validation
- [ ] Add more feature engineering
- [ ] Create web UI for predictions
- [ ] Add model versioning
- [ ] Implement A/B testing framework
- [ ] Add monitoring and alerting
- [ ] Deploy to production environment

---

**Last Updated:** December 2025  
**Model Version:** 1.0.0
