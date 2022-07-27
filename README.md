CLTV Prediction with BG-NBD and Gamma-Gamma

Business Problem

FLO wants to set a roadmap for sales and marketing activities. In order for the company to make a medium-long-term plan, it is necessary to estimate the potential value that existing customers will provide to the company in the future.

The dataset consists of information obtained from the past shopping behaviors of customers who made their last purchases as OmniChannel (both online and offline shopper) in 2020 - 2021.

- master_id: Eşsiz müşteri numarası
- order_channel : Alışveriş yapılan platforma ait hangi kanalın kullanıldığı (Android, ios, Desktop, Mobile, Offline)
- last_order_channel : En son alışverişin yapıldığı kanal
- first_order_date : Müşterinin yaptığı ilk alışveriş tarihi
- last_order_date : Müşterinin yaptığı son alışveriş tarihi
- last_order_date_online : Muşterinin online platformda yaptığı son alışveriş tarihi
- last_order_date_offline : Muşterinin offline platformda yaptığı son alışveriş tarihi
- order_num_total_ever_online : Müşterinin online platformda yaptığı toplam alışveriş sayısı
- order_num_total_ever_offline : Müşterinin offline'da yaptığı toplam alışveriş sayısı
- customer_value_total_ever_offline : Müşterinin offline alışverişlerinde ödediği toplam ücret
- customer_value_total_ever_online : Müşterinin online alışverişlerinde ödediği toplam ücret
- interested_in_categories_12 : Müşterinin son 12 ayda alışveriş yaptığı kategorilerin listesi

TASK 1: Preparing the Data

     1. Read the flo_data_20K.csv data. Make a copy of the dataframe. 
     2. Define the outlier_thresholds and replace_with_thresholds functions required to suppress outliers.
     Note: Frequency values must be integer when calculating cltv. Therefore, round the lower and upper limits with round(). 
     3. Suppress "order_num_total_ever_online","order_num_total_ever_offline","customer_value_total_ever_offline","customer_value_total_ever_online" if there are outliers.
     4. Omnichannel means that customers shop from both online and offline platforms. Create new variables for each customer's total purchases and spend. 
     5. Examine the variable types. Change the type of variables that express date to date.

TASK 2: Creating the CLTV Data Structure
           
           1. Take 2 days after the date of the last purchase in the data set as the date of analysis.
           Create a new cltv dataframe with the values 
           
           2.customer_id, recency_cltv_weekly, T_weekly, frequency and monetary_cltv_avg.
           Monetary value will be expressed as average value per purchase, recency and tenure values will be expressed in weekly terms.
           
TASK 3: BG/NBD, Establishing Gamma-Gamma Models, Calculating CLTV
            
            1. Fit the BG/NBD model.
                
                a. Estimate expected purchases from customers in 3 months and add exp_sales_3_month to cltv dataframe.
                b. Estimate expected purchases from customers in 6 months and add exp_sales_6_month to cltv dataframe.
                
            2. Fit the Gamma-Gamma model. Estimate the average value of the customers and add it to the cltv dataframe as exp_average_value.
            
            3. Calculate 6 months CLTV and add it to the dataframe with the name cltv.
            
                 a. Standardize the cltv values you calculated and create the scaled_cltv variable.
                 b. Observe the 20 people with the highest Cltv value.

TASK 4: Creating Segments by CLTV
          
          1. Divide all your customers into 4 groups (segments) according to the 6-month standardized CLTV and add the group names to the dataset. Add it to the dataframe with the name cltv_segment.
          
          2. Make short 6-month action suggestions to the management for 2 groups you will choose from among 4 groups.

TASK 5: Functionalize the whole process.                 
