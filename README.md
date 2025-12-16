# **E-commerce Sales Optimization Project**

## **Introduction**
This project was developed for the **Data Analysis Algorithms** course at **Helwan National University**.  
This is a team project. Refer to [Credits](#credits)[^.].
##  **Problem Definition**
Amazon is one of the largest e-commerce platforms globally, our objective is to analyze Amazon sales dataset and provide useful information about **sales trends** and **customer behavior** in order to **maximize revenue**.

<img src="https://i.guim.co.uk/img/media/afe2167c8989b94f2f20fec2886f35aa8dd1279f/158_288_3316_1991/master/3316.jpg?width=620&dpr=2&s=none&crop=none" width="55%" alt="Amazon Logo Photo">   


> [Image by The Guardian](https://www.theguardian.com/technology/2022/jul/06/uk-watchdog-opens-investigation-into-amazon-marketplace-practices)

---

### **Dataset Description**
- The dataset provides detailed information on **42,000+** Amazon electronics products, including sales, ratings and pricing.
- Raw, original data, with alot of missing values and inconsistent entries, which makes it ideal for preprocessing practice and feature engineering.   
> [**Dataset on Kaggle**](https://www.kaggle.com/datasets/ikramshah512/amazon-products-sales-dataset-42k-items-2025?select=amazon_products_sales_data_uncleaned.csv)

##### **Features**:


1. **title** – Complete name/title of the product
1. **rating** – Average customer rating (numeric) out of 5
1. **number_of_reviews** – Total number of customer reviews
1. **bought_in_last_month** – Units purchased in the last month
1. **current/discounted_price** – Current price after applying discount
1. **price_on_variant** – Price of product variations
1. **listed_price** – Original listed price before discount
1. **is_best_seller** – Indicates if the product is tagged as a Best Seller
1. **is_sponsored** – Whether the product is a Sponsored item or Organic
1. **is_couponed** – Special discounted coupons
1. **buy_box_availability** – BuyBox button availability on Amazon
1. **delivery_details** – Estimated delivery date
1. **sustainability_badges** – Eco-friendly and sustainability-related tags
1. **image_url** – Direct image link of the product
1. **product_url** – Official Amazon product page URL
1. **collected_at** – Date when the data was collected  

## **Objective Tasks**
- **Data Wrangling** ⟶ Clean dataset, handle missing values,
duplicates, outliers, inconsistent formats.
- **Exploratory Data Analysis (EDA)** ⟶ Perform univariate & multivariate analyses.
Use appropriate visualizations with insights.
- **Feature Engineering & Selection** ⟶ Create new features, encode variables, apply
selection methods (filter, Lasso, RFE).
- **Probability  & Hypothesis Testing** ⟶ Fit distributions, calculate probabilities, and conduct hypothesis tests relevant to dataset.
- **Dimensionality Reduction (PCA)** ⟶ Apply PCA, interpret components, visualize clusters/patterns.
---

## **Technical Approach**
The following section discusses the technical implementation of the required objectives with details and the tools used to address them.  
Proceed to the [**Full notebook**](https://colab.research.google.com/drive/1Ww31zrvAM92Hng-qRkJR8PCQFcZjnyat?usp=sharing) to see the implementation.
#### **Tools:**
- **Google Colab** ⟶ Used to write code in `.ipynb` format that can be accessed and edited by the team.
- **Python Libraries** ⟶ Used libraries like `pandas`, `matplotlib`, `seaborn` to handle, analyze and visualze the data.
- **Github** ⟶ Used to save named versions of the notebook and to write and show the `README` file.

---



### **Data Cleaning**
- We started with loading the data using `KaggleDatasetAdapter` into a pandas dataframe.


- Handled inconsistent formats:
  - |           |  number_of_reviews |  bought_in_last_month    | price_on_variant             | listed_price |
    | ----------|:------------------:|:------------------------:|:----------------------------:| :-----------:|  
    | Old format| 3,044              | 2K+ bought in past month	| basic variant price: $162.24 | \$159.00     |  
    | New format| 3044               | 2000	                    | 162.24                       | 159.00       |


- Converted data types for columns:
    - | | product_rating |  number_of_reviews| bought_in_last_month | current/discounted_price |  price_on_variant |  listed_price | delivery_details | collected_at|   
      | --|:---------------:|:-------------------:|:----------------------:| :---------------:|:---------------:|:---------------:| :----------------------: | :---------------:|
      Old datatype | object | object | object | object | object | object | object | object | 
      New datatype | float | int | int | float | float | float |  datetime | datetime

      > All the invalid data converted to **NaN** using  `errors='coerce'`.  

  

- Handled Missing values:
  - Used data from **current/discounted_price**, **price_on_variant**, **listed_price** to fill the missing values in **current/discounted_price** and **listed_price**. 
  - Filled missing values in **rating** with `mean` since the column has limited outliers.     
  - Filled missing values in **numeric columns**
  with `median` because it's less sensetive to **outliers**.     
  - Filled missing values in delivery_details with the value in the previous row using `ffill`.
  - Filled missing values in **buy_box_availability** with "not available".

- Column Additions and Deletions
  - Created new column `discount` that represents the discount percentage for products.
  - Created new column `category` to split products into **15 categories** based on keywords in the product title.
  - Created new columns `OrderYear`,`OrderMonth`,`OrderDayOfWeek` derived from **delivery_details**.
  - Dropped **current\discounted price** and **price_on_variant**, as **listed_price** and discount are sufficient.
  - Dropped **sustainability_badges** since `nan > 90%`.
  - Dropped **image_url** and **product_url**.

  - Column Renaming:
    












### **Exploratory Data Analysis [EDA]**
- We performed univariate and multivariate analyses to gain insights.
- Used `matplotlib` and `seaborn` to make informative visualizations.ol
- 
### **Feature Engineering & Selection**
### **Hypothesis Testing**
### **Dimensionality Reduction**

## Credits
[**`Yousef Medhat`**](https://www.linkedin.com/in/yousef-medhat-7293232a1/)  
[**`Yousef Waheed`**](https://www.linkedin.com/in/youssef-waheed-8462061a7/)  
[**`Ali Abdou`**](https://www.linkedin.com/in/ali-abdouu/)  
[**`Amira Azzam`**](https://www.linkedin.com/in/yousef-medhat-7293232a1/)  
[**`Maria Gerges`**](https://www.linkedin.com/in/maria-gerges-81b04a30a/)
[^.]: d
## **License**
This project is open source and available under the [MIT License](https://mit-license.org/).
