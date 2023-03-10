# PHONEPE_PULSE_DATA_VISUALIZATION - PROJECT 2

# Required libraries to be imported
```python
import streamlit as st
from PIL import Image
import os
import json
from streamlit_option_menu import option_menu
import pandas as pd
import sqlite3
import plotly.express as px
```
# For cloning data using this command
```python
import requests
response = requests.get(url)
repo = response.json()
clone_url = repo['clone_url']
repo_name = "pulse"
clone_dir = os.path.join(os.getcwd(), repo_name)
```
# Creating dataframes using Pandas
```python
clm={'State':[], 'Year':[],'Quater':[],'Transaction_type':[], 'Transaction_count':[], 'Transaction_amount':[]}
for i in Agg_state_list:
    p_i=path+i+"/"
    Agg_yr=os.listdir(p_i)
    for j in Agg_yr:
        p_j=p_i+j+"/"
        Agg_yr_list=os.listdir(p_j)
        for k in Agg_yr_list:
            p_k=p_j+k
            Data=open(p_k,'r')
            D=json.load(Data)
            for z in D['data']['transactionData']:
              Name=z['name']
              count=z['paymentInstruments'][0]['count']
              amount=z['paymentInstruments'][0]['amount']
              clm['Transaction_type'].append(Name)
              clm['Transaction_count'].append(count)
              clm['Transaction_amount'].append(amount)
              clm['State'].append(i)
              clm['Year'].append(j)
              clm['Quater'].append(int(k.strip('.json')))

# Successfully created a dataframe
df_aggregated_transaction=pd.DataFrame(clm)
```
# Create the app using streamlit[Reference](https://docs.streamlit.io/library/api-reference)\
# Visualizing the data with plotly and streamlit
```python
 fig=px.bar(df,x=column name,y=column name)
            tab1, tab2 = st.tabs(["Streamlit theme (default)", "Plotly native theme"])
            with tab1:
                st.plotly_chart(fig, theme="streamlit", use_container_width=True)
            with tab2:
                st.plotly_chart(fig, theme=None, use_container_width=True)
```
# Visualization of the Phonepe_pulse_data
![Screenshot 2023-03-10 061726](https://user-images.githubusercontent.com/115634164/224194885-12a56621-1f6e-482d-9f16-74ecf3153ac9.png)
![image_2023-03-10_062004520](https://user-images.githubusercontent.com/115634164/224194931-5e181016-98c6-4262-8cb4-0ed17bc927dc.png)

# You can now view your Streamlit app in your browser.
'''Local URL: http://localhost:8501
  Network URL: http://192.168.0.102:8501'''
    


