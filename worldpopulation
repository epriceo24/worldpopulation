import streamlit as st 
import pandas as pd
import numpy as np

st.title('World Population')

@st.cache_data
def load_data():
    data = pd.read_csv('world_population.csv')

    #rename columns
    data.columns = ['Rank', 'Country Code', 'Country', '2022 Population', '2020 Population', '2015 Population', 'Area (km²)', 'Density (per km²)', 'Growth Rate', 'World Population Percentage']

    return data

data = load_data()

#create unique list of countries
countries = ['All'] + list(pd.unique(data['Country'].values.ravel('K')))
countries = [country for country in countries if country != '']

#multiselect country
selected_countries = st.multiselect('Select countries', countries)

#filter data
filtered_data = data[(data['Country'].isin(selected_countries))]

#st.write the intial data and then the filtered data when selected
st.write(filtered_data if selected_countries else data)
