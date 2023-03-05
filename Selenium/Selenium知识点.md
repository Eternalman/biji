## Selenium

### 1.安装Selenium

```python
Pip install selenium
```

### 2.启动浏览器

```python
# 导入webdriver类
from selenium import webdriver
# 调用控制插件
driver = webdriver.Chrome()
# 启动浏览器
driver.get("http://www.baidu.com")
```

### 3.模拟用户操作

#### 3.1浏览器对象的方法

```python
1.browser = webdriver.Chrome() #启动浏览器

2.browser.quit() # 关闭整个浏览器

3.browser.close() #关闭当前浏览器

4.browser.get(url) # 发送get请求

5.browser.page_source # HTML结构源码

6.browser.page_source.find('字符串') #从html源码中搜索指定字符串,没有找到返回-1

7.browser.execute_script('javascript') # 执行脚本

8.browser.save_screenshot('baidu.png') #获取快照

9.browser.execute_script('window.scrollTo(0,document.body.scrollHeight)') # 浏览器下拉到底部
```

#### 3.2定位操作

**find_element**找到的是WebElement节点对象，但是没找到会抛出ElementException异常。 **find_elements**返回一个列表，列表里元素是WebElement节点对象**find_elements**如果没有找到，它返回一个空列表

| Webdriver By                 | 含义                        |
| ---------------------------- | --------------------------- |
| find_element_by_xpath()      | 根据xpath查找，获取一个对象 |
| find_elements_by_xpath()     | 根据xpath查找，获取对象列表 |
| find_element_by_id()         | 根据id查找，获取一个对象    |
| find_element_by_class_name() | 根据class属性名查找         |

另外一种定位：

| Webdriver By                      | 含义                                          |
| --------------------------------- | --------------------------------------------- |
| find_element/s(By.XPATH," ")      | 根据xpath查找，获取一个对象or获取多个对象(+s) |
| find_element/s(By.ID," ")         | 根据id查找，获取一个对象                      |
| find_element/s(By.CLASS_NAME," ") | 根据class属性名查找                           |
| find_element/s(By.LINK_TEXT," ")  | *匹配超链接载体*  --匹配超链接                |

#### 3.3节点对象操作

```python
 1.ele.send_keys('') 搜索框发送内容
 2.ele.click() 点击
 3.ele.text 获取文本内容，包含子节点和后代节点的文本内容
 4.ele.get_attribute('src') 获取属性值
```

#### 3.4切换页面

**适应网站**

页面中点开链接出现新的页面，但是浏览器对象browser还是之前页面的对象

```python
# 获取当前所有句柄（窗口）
all_handles = browser.window_handles

# 切换browser到新的窗口，获取新窗口的对象
browser.switch_to.window(all_handles[1])

# 设置窗口最大化
browser.maximize_window() 
```

#### 3.5获取图片的链接并保存

```py
img = i.find_element_by_xpath('.//div[1]/a/img') # xpath定位到图片
lian = jmg.get_attribute('src') # 获取图片的src
jpg = requests.get(lian).contert # 获取到图片

    with open(r'xxx\\' + '.jpg', 'wb') as j:
        j.write(jpa)
```

