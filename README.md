# test.gmail
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import unittest
from test.test_robotparser import PasswordProtectedSiteTestCase

class SendemailTest(unittest.TestCase):


    def setUp(self):
        self.driver = webdriver.Chrome()
        self.driver.implicitly_wait(30)
        self.driver.maximize_window()

    def test_sendWithCorrectRecipientTest(self):
        
        #given
        driver = self.driver
        self.loginToGmailAccount('karolina.korbas1@gmail.com', 'password')

        #and
        composeButton = driver.find_element_by_xpath("//div[contains(@text, 'COMPOSE')]")
        composeButton.click()
        self.driver.implicitly_wait(3000) 
        
        #and
        recipientField= driver.find_element_by_name("to")
        recipientField.send_keys("test.mail12345@gmail.com")
       
        #and
        emailtext = driver.find_element_by_class_name("Am Al editable LW-avf")
        emailtext.send_keys("This is message.")
        
        #and
        
        sendButton= driver.find_element_by_id("118")
        sendButton.click()
        self.driver.implicitly_wait(3000) 


Assert(river.find_by_class_name("vh").text == "Your message has been sent. View message”)
