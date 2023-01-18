import unittest
import time
from selenium import webdriver 
from selenium import webdriver
driver = webdriver.Chrome()
from selenium.webdriver.common.by import By
from webdriver_manager.chrome import ChromeDriverManager

driver.browser = webdriver.Chrome(ChromeDriverManager().install())

#Access page
driver.get("http://barru.pythonanywhere.com/daftar")
browser = driver.browser #buka web browser
browser.get("http://barru.pythonanywhere.com/daftar") # buka situs
time.sleep(3)

#Successfully Login
driver.get("http://barru.pythonanywhere.com/daftar")
browser = driver.browser #buka web browser
browser.get("http://barru.pythonanywhere.com/daftar") # buka situs
time.sleep(2)
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
    
#Failed Login 
browser = driver.browser #buka web browser
browser.get("http://barru.pythonanywhere.com/daftar") # buka situs
time.sleep(2)
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

#Successfully Sign Up
browser = driver.browser #buka web browser
browser.get("http://barru.pythonanywhere.com/daftar") # buka situs
time.sleep(1)
browser.find_element(By.ID,"signUp").click() # klik tombol sign up
time.sleep(1)
browser.find_element(By.ID,"name_register").send_keys("Angga") # isi nama
time.sleep(1)
browser.find_element(By.ID,"email_register").send_keys("angga@mailinator.com") # isi email
time.sleep(1)
browser.find_element(By.ID,"password_register").send_keys("Test123") # isi password
time.sleep(1)
browser.find_element(By.ID,"signup_register").click() # klik tombol sign up
time.sleep(1)

response_data = browser.find_element(By.ID,"swal2-title").text
response_message = browser.find_element(By.ID,"swal2-content").text

ddriver.assertIn('Berhasil', response_data)
driver.assertEqual(response_message, 'Created User')
    
    
unittest.main()
