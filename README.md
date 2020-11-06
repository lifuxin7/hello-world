# python+selenium实现网站自动登录（初）
#-*- coding:utf-8 -*-
from time import sleep
from selenium import webdriver

myusername = "abcdefg"
mypassword = "abcdefg"

wd = webdriver.Chrome()
#设置最大等待时长
wd.implicitly_wait(10)

def main():
    # 起点中文网
    wd.get('https://www.qidian.com/')

    # 点击登录
    wd.find_element_by_id('login-btn').click()
    sleep(3)
    #切换到弹出的窗口
    wd.switch_to.frame('loginIfr')
    # 输入账号
    idInput = wd.find_element_by_xpath("//*[@id='username']")
    idInput.clear()
    idInput.send_keys(myusername)
    # 输入密码
    pwdInput = wd.find_element_by_id('password')
    pwdInput.clear()
    pwdInput.send_keys(mypassword)
    # 点击登录
    wd.find_element_by_xpath("//a[@class='red-btn go-login btnLogin login-button']").click()

    sleep(30)
    cookies = driver.get_cookies()
    print (cookies)

main()
