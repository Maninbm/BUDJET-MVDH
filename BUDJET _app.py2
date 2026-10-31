import streamlit as st
import pandas as pd

st.set_page_config(page_title="Simple Budget App", page_icon="💰")

st.title("💰 எளிய பட்ஜெட் செயலி")

if 'transactions' not in st.session_state:
    st.session_state.transactions = []

trans_type = st.selectbox("வகை", ["வரவு (Income)", "செலவு (Expense)"])
category = st.text_input("பிரிவு (உதா: உணவு, சம்பளம்)")
amount = st.number_input("தொகை (₹)", min_value=0.0)

if st.button("பதிவு செய்"):
    if category and amount > 0:
        actual_amount = amount if trans_type == "வரவு (Income)" else -amount
        st.session_state.transactions.append({
            "வகை": trans_type,
            "பிரிவு": category,
            "தொகை": actual_amount
        })
        st.success("சேமிக்கப்பட்டது!")
        st.rerun()

if st.session_state.transactions:
    df = pd.DataFrame(st.session_state.transactions)
    total_balance = df["தொகை"].sum()
    
    st.metric("மீதமுள்ள இருப்பு", f"₹ {total_balance:,.2f}")
    st.dataframe(df, use_container_width=True)
