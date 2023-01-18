# Sanbercode---Tugas-day-17--Ria-Ristia
Tugas day 17 - Ria Ristia
Case 1: Access url 

from selenium import webdriver
driver1 = webdriver.Chrome()
driver2 = webdriver.Chrome()
driver1.get("https://www.saucedemo.com/")
driver2.get("http://barru.pythonanywhere.com/daftar")

Case 2: Successfully Login

import unittest
import time
from selenium import webdriver 
from selenium import webdriver
driver = webdriver.Chrome()
from selenium.webdriver.common.by import By
from webdriver_manager.chrome import ChromeDriverManager
driver.browser = webdriver.Chrome(ChromeDriverManager().install())
driver.get("http://barru.pythonanywhere.com/daftar")
browser = driver.browser #buka web browser
browser.get("http://barru.pythonanywhere.com/daftar") # buka situs
time.sleep(3)
browser.find_element(By.XPATH,"/html/body/div/div[2]/form/input[1]").send_keys("riaristia@gmail.com") # isi email
time.sleep(1)
browser.find_element(By.CSS_SELECTOR,"input#password").send_keys("test123") # isi password
time.sleep(1)
browser.find_element(By.ID,"signin_login").click() # klik tombol sign in
time.sleep(1)

response_data = browser.find_element(By.ID,"swal2-title").text
response_message = browser.find_element(By.ID,"swal2-content").text

driver.assertIn('Welcome', response_data)
driver.assertEqual(response_message, 'Anda Berhasil Login')

Case 3: Login without email and password

browser = driver.browser #buka web browser
browser.get("http://barru.pythonanywhere.com/daftar") # buka situs
time.sleep(3)
browser.find_element(By.XPATH,"/html/body/div/div[2]/form/input[1]").send_keys("") # isi email
time.sleep(1)
browser.find_element(By.CSS_SELECTOR,"input#password").send_keys("") # isi password
time.sleep(1)
browser.find_element(By.ID,"signin_login").click() # klik tombol sign in
time.sleep(4)

response_data = browser.find_element(By.ID,"swal2-title").text
response_message = browser.find_element(By.ID,"swal2-content").text

driver.assertIn('tidak valid', response_data)
driver.assertEqual(response_message, 'email atau password anda salah')
