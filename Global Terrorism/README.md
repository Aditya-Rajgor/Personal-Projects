
# Final Project of the year 2020 #
## The project is simply an Exploratory Data Analysis on Global Terrorism Database. I've wrote medium article about this full project, this is the repository for that particular article. ##

### Let's start ###

   So, this project was originally my internship project, but it wasn't compulsory and also they provided me outdated data. Therefore I went to the original website for the latest data. Unfortunately latest data (1970 to 2019) was only available for commercial license holders on the moment. I reported this to my internship mentors but no help. So I had to go with (1970 to 2018) database. This is why I consider this my personal project, although one fellow intern helped me correcting my article's english. But that doesn't count as contribution. does it?
   
   Anyway let's get to the business. The database is really huge (df.shape (191464,135)) Creators owns my respect. Even after doing my analysis I highly feels like there is lots of things to uncover. All I've did is very direct and specific. 

[<img src = 'images/medium_logo.png' height='59px' width='50px'>](https://adityarajgor.medium.com/inside-the-global-terrorism-database-967084386a16)
 
    
## Issues with current analysis
 1. All the graphs are made upon number of counts (This only shows how often they occurs not acutual fatality those attacks caused)
    * Solution would be to make bar chart showing kills and Injured.
 2. In choropleth map countries are missing 
    * Actual countries 
       ```
       In[10] : np.count_nonzero(country_map_df['country'].unique())
       ```
       ```
       Out[10] : 204
       ```
    * On the map
      ```
       In[10] : np.count_nonzero(country_map_df['country_codes'].unique())
       ```
       ```
       Out[10] : 162
       ```
    This causing russia not to show on the choropleth map. It's because russia and soviet union both are separate in the database.
    * Solution would be include all other country codes manually.
    
 3. Not proper use of latitude and longitude
   * The plan was to make heat map of casualty for all years which have a "Play" button. By pressing it it will show all the casualty on geographical map               throughout all years.
   
4. Comparision between two to five countries 
   * I saw this type of chart somewhere recently, and it was incredible. it will be really great to see two or more countries side by side for any reason.
   
  
   
   
