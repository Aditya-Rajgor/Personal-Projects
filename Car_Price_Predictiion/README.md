[![Gmail][Gmail-shield]][Gmail-url]
[![LinkedIn][linkedin-shield]][linkedin-url]
[<img src="https://www.analyticsvidhya.com/wp-content/uploads/2015/06/kaggle-logo-transparent-300.png" width="60" height="30"/>][kaggle-url]

## About The Compitition
We all know about legendary movie **Titanic**,that romatic story is unfortunately fictional, but the disaster was real.
On April 15, 1912, the widely considered “unsinkable” RMS Titanic sank after colliding with an iceberg. Unfortunately, there weren’t enough lifeboats for everyone onboard, resulting in the death of 1502 out of 2224 passengers and crew.
While there was some element of luck involved in surviving, it seems some groups of people were more likely to survive than others.
Kaggle provides us train and test data sets, which containts details like **Sex,Age,Passenger Class,Embarked etc**,.Our job is to find who had survived in test data set.

<!-- PROJECT LOGO -->
![car-image](images/ultr.jpg)


<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About the Compitition](#about-the-compitition)
* [Brief Overview](#brief-overview)
* [What If You were on Titanic?](#what-if-you-were-on-titanic)
* [Deployment of Titanic Survivor Classifier](#deployment-of-titanic-survivor-classifier)
* [Deployment Dependencies](#deployment-dependencies)
* [Libraries used in Jupyter Notebook](#Libraries-used-in-jupyter-notebook)


```python
df[df['Kms_Driven']==500000]
```
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Car_Name</th>
      <th>Year</th>
      <th>Selling_Price</th>
      <th>Present_Price</th>
      <th>Kms_Driven</th>
      <th>Fuel_Type</th>
      <th>Seller_Type</th>
      <th>Transmission</th>
      <th>Owner</th>
      <th>Price_Diff</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>196</th>
      <td>Activa 3g</td>
      <td>11</td>
      <td>0.17</td>
      <td>0.52</td>
      <td>500000</td>
      <td>Petrol</td>
      <td>Individual</td>
      <td>Automatic</td>
      <td>0</td>
      <td>0.35</td>
    </tr>
  </tbody>
</table>
</div>
## Brief Overview
In data set there are **missing values**, some hidden but important features like name **Prefix,Family Size**,which plays good role predicting person's survive chance,
we imputed missing values with **Random Forest Regressor** which is way more accurate than filling with **Mean,Median or most frequent value(Mode)**.
Then we used different models and tune them and pick the best model for our final prediction.
```sh
df.isna().sum()
```
```sh
PassengerId      0
Survived       418
Pclass           0
Sex              0
Age            263
SibSp            0
Parch            0
Ticket           0
Fare             1
Embarked         2
```
**Filling Fare with median value 'cause there is too many outliers to affect our mean**
<div>
    <a href="https://plotly.com/~Aditya1112/1/?share_key=XvEsaVIjQk5BfDfei4pvWg" target="_blank" title="box" style="display: block; text-align: center;"><img src="https://plotly.com/~Aditya1112/1.png?share_key=XvEsaVIjQk5BfDfei4pvWg" alt="click to redirect" style="max-width: 100%;width: 800px;"  width="800" onerror="this.onerror=null;this.src='https://plotly.com/404.png';" /></a>
</div>

**Family Size,Name Prefix and Their Survive Chance**

![FamSize-Survive](Graphs/familysize.png)   ![Prefix-Survive](Graphs/prefix.png)

**Family Size with 2,3 and 4 had higher chance of Survive,**

**Similarly,prefix Mr[Married Man :(  ] had very low chance of Survive**

**Tuning Diffrent model and predict the future with best model**

KNN model's accuracy over K values
<div>
    <a href="https://plotly.com/~Aditya1112/3/?share_key=ELO7dxrEVylMHSaYk1tPKp" target="_blank" title="knn_lie" style="display: block; text-align: center;"><img src="https://plotly.com/~Aditya1112/3.png?share_key=ELO7dxrEVylMHSaYk1tPKp" alt="knn_line" style="max-width: 100%;width: 700px;"  width="700" onerror="this.onerror=null;this.src='https://plotly.com/404.png';" /></a>
</div>

After some try and error **Random Forest** stand out
```sh
confusion_matrix(y_test,y_pred_rfc)
```
Output:
```sh
array([[268,   5],
       [  2, 171]])
```
**Feature Importance**:
![feature-importance](Graphs/rf_feature_importance.png)

Prefix Mr,Sex_male and Passenger Class are **Highly correlate** to Wheather pearson survive or not.


# What If You were on Titanic?
Suppose you were on Titanic (1912) and you are using widest network sim Airtel.you want to know weather you survive or not if titanic disaster happen. Let's figure out by given heroku app link.

### Deployment of Titanic Survivor Classifier
For deployment I've used full titanic dataset rather than only training datase to make performance much better. 
Final Heroku app takes some user inputs like Passenger Class,Age,Sex,etc,.And predict weather person will Survivr or Not using Machine Learning Model. It's completly based on previous titanic data and being predict by Random Forest algorythm's patterns. Trainnig accuracy is 77.07%, there is always some errors in predictons but we are more confidence with these results.


[<img src="https://cdn.worldvectorlogo.com/logos/heroku.svg" width="100" height="64" />][heroku-url]



### Deployment Dependencies:
 * PyCharm
 * Django
 * Heroku
 * Joblib
 * postgresql
 * gunicorn
 
### Libraries used in Jupyter Notebook
* Pandas
* Numpy
* Seaborn,Matplotlib
* Plotly
* Dataprep
* Sklearn
* xgboost




[Titanic Data Set](https://www.kaggle.com/c/titanic)

background image source:History-uk.com: The Sinking of RMS Titanic


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[kaggle-url]: https://www.kaggle.com/adityarajgor
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/aditya-rajgor
[product-screenshot]: https://miro.medium.com/max/2000/0*TVXbu3DbzLtnfGRk.jpg
[Gmail-Shield]:https://img.shields.io/badge/Email-red.svg?logo=data:image/webp;base64,UklGRmoFAABXRUJQVlA4TF0FAAAv/8A/EJAYSZIiSa6/2AdDWXCPEyEJ///zbT7BP7WC4f/PjFSnNT3O3q22bRx5nVX36OPsLTvVtm23cZ42+X/lQJKkSJLnkcR3/5lL1jKsn9d/b8SwopTTmKNlReuEldYcjXKxztxGLl8vHq0WvF6F5HfgVDKiBcOkCncVRgkDWjKMSkgu4W0QLRpDfC4QRI9WDb2gU7LY0LJhk332jBaOrEMC2TbGJvDovdGjlUPP+xsSg2jpGCT5SglaO4q/tk3GvTHgPqlCi0clAJAzbY6RDEAhWj0KAPQm6KSEkYLTnqAHcJnLGWy5ORHXbWYuh8CKRpk4VjgPeY5RJqKUo1S0cJoFR00oFeU0we3u8iRcDDZnGnMoF/uezMFj+yjHLF10uSkjmAGBkuhqTl/A7iv3CXDzKXxxPArHNN/++JjsPt6Fdie4/0UmeK+IOyPyHI8GiP8UfZH7h2aIZf5dUVtEU4RZUk8SRrnAQB27fkhUo8qZcIpjtaNpYsvNdiN7njhS0IlcR2ikaG4zxTlqnOvqbJfajOzyGW6Ke2SvwZWZo01xAsXj3SLMF27FR7aPaL6Y4jvByO4+xYXUJYhuyhv3eUm0ycj2PXRpbskpTu5v6JLBPMLQP/SW+NfDz0LmUkVFBHkA7trOTHGJ1YhnymwhdwEqAJw2FIladv1HtlYcFAEYb0NTHNd8ZOO9wUAZAEJoUSI23Swzsm1krlARDFAJUBnJTHH5jUe2YVehGOCosesU5xD6ejVwgnIApLO0nOIuGMj8pycVoCKgttBwinuYGdkW+EFRQOp7aop3G9m+8YCyIFVCfeaWG9mpqgmFxUqoKT4ZvE3GqmZluRJKLyQzslNVszzAeNtjihN5ho98dd5ioLhoCaWheHpkx6pmddkSaon6Sa5ZyFRNKmgDOGrItCEJzxHHlKqaDcRLqFqSh0a2KpQIizSAXoDaPEpEB+6Rka0tUzWpoYcCJdSGmw+MbOupqtlEhRLqSN5dchxFqqZiAuiiRgnVxPHWyNYQq5pdAU5r5u5uLhYb2dpw0BhgvInUQ3ueXB/ZqarZSZkSyqaU4NLIVhT5Z4xOMEArhUqoT9zOcfUhVTWbqVRCTfE+w8tEqmqOAEA6c2aK50c2i3SAdmqVULwXB1OcyFN8qGo2VK2E+vdtipP7k6qaHZUroZaocyObVTEhDAPAXVupKS6OKVU1B1DkEkk1mZGtlRK6KllCU1VzKACCaTugEwIwF6AyUp8RKuisXAlNVc3WqpXQVNXsrVgJDVXNEQGpb2VvAkkK7VUqoamqOSYAd2zVY8s9gEkBTms12ihhBE+X0GpVcwaPl9BaVXNiQGW4UNUcGnBUX4NGTjA2AGnMNarmIDIltEDVHB6Q+hqvmrNoV0JZlRDCMHIlNFk1dwA4rbGqOY9WJRTvHQYWASCINlE1J9KohBqhgpn0KaGaOMFQ8iX0yao5lSYl1CI1zKVHCfWdFBYDBIpYn6iakylSQu9Xze0ATuvNqjmc8iX0o2pOp3gJpRMKsCVw1fAVRqlgQKVLqCZOsCoAqcwnVVMGwIjqllCL/GFhQOrrYdWcUsES+r1qjqlmCbXtPsDeAKtVOyWsDjAYWB7A67/Xf6//fgdi3R4r3fZozW3PLM32/FO+Pe9Fb08UDr87PBb07k4PgIL1z11Izrj9uRtB5eZUAADgGBY/dycWPqN48XOXbn/uVgOY7c9dy2v/c/ceRebC8LLgODLZ1n1bFpxFwLbnrhYI5+FlYNUPxPvaQwApYlizbSu+fP4BrIoV32BSiYUbIZOvZ7tz1+tRQAZ347TItc7db9Y/5aIpYf28/nshBgA=
[Gmail-url]: https://mail.google.com/mail/u/1/#drafts?compose=CllgCJlKGNbfJVvjLtXzkhpsgDbnCgcQtLVRtskFLsxFRcdQvxNGhbSjqLBlqdmJxrHKscPrwQV
[heroku-url]: https://titanic101.herokuapp.com/
