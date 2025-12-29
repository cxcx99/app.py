# app.py
import streamlit as st

st.title("FIND OUT YOUR CAREER PATH")

score_programmer = 0
score_designer = 0
score_datascientist = 0

# Soal 1
st.subheader("Jenis pelajaran apa yang kamu sukai di sekolah")
q1 = st.radio("1. Pilih satu:", [
    "Ilmu eksakta e.g Matematika, Fisika",
    "Pelajaran yang mengedepankan kreativitas, e.g seni",
    "Suka keduanya"
], key="q1")

# Soal 2
st.subheader("Mana yang menurut kamu lebih penting dalam sebuah aplikasi")
q2 = st.radio("Pilih satu:", [
    "Fungsionalitas fitur yang berjalan baik",
    "Tampilan aplikasi yang menarik dan mudah dipahami",
    "Akurasi informasi dan data yang disajikan"
], key="q2")

# Soal 3
st.subheader("Kamu menemui seseorang dalam masalah. Apa yang kamu lakukan untuk menyelesaikan masalah tersebut")
q3 = st.radio("Pilih satu:", [
    "Bertanya kepada orang lain atau komunitas yang pernah mengalami kendala serupa untuk mengetahui penyelesaian",
    "Meminta orang tersebut untuk menceritakan kembali masalahnya kepada saya agar saya dapat menarik solusi yang sesuai",
    "Mengumpulkan informasi dari berbagai sumber terkait masalah tersebut dan menarik solusi"
], key="q3")

if st.button("Submit"):
    # Skoring berdasarkan jawaban
    if q1 == "Ilmu eksakta e.g Matematika, Fisika":
        score_programmer += 1
    elif q1 == "Pelajaran yang mengedepankan kreativitas, e.g seni":
        score_designer += 1
    else:
        score_datascientist += 1

    if q2 == "Fungsionalitas fitur yang berjalan baik":
        score_programmer += 1
    elif q2 == "Tampilan aplikasi yang menarik dan mudah dipahami":
        score_designer += 1
    else:
        score_datascientist += 1

    if q3 == "Bertanya kepada orang lain atau komunitas yang pernah mengalami kendala serupa untuk mengetahui penyelesaian":
        score_programmer += 1
    elif q3 == "Meminta orang tersebut untuk menceritakan kembali masalahnya kepada saya agar saya dapat menarik solusi yang sesuai":
        score_designer += 1
    else:
        score_datascientist += 1

    # Hasil akhir
    st.subheader("RESULTS:")
    if score_programmer > score_designer and score_programmer > score_datascientist:
        st.markdown(''':blue[YOUR CAREER PATH:]:green-background[A PROGRAMMER]''')
        st.snow()
    elif score_designer > score_programmer and score_designer > score_datascientist:
        st.markdown(''':blue[YOUR CAREER PATH:]:yellow-background[AN UI/UX DESIGNER]''')
        st.snow()
    elif score_datascientist > score_designer and score_datascientist > score_programmer:
        st.markdown(''':blue[YOUR CAREER PATH:]:red-background[A DATA SCIENTIST]''')
        st.snow()
    else:
        st.markdown(''':rainbow[YOU CAN BE ANYTHING! A PROGRAMMER, UI/UX DESIGNER, OR DATA SCIENTIST. CHOOSE WISELY!]''')
        st.snow()
