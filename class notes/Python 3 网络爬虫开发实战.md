# Python 3 网络爬虫开发实战

Class: Programming
Created: March 21, 2022 2:17 PM
Materials: Python%203%20%E7%BD%91%E7%BB%9C%E7%88%AC%E8%99%AB%E5%BC%80%E5%8F%91%E5%AE%9E%E6%88%98%20b64bc049b6684b03a816d19dcd58faa6/Python_3%E7%BD%91%E7%BB%9C%E7%88%AC%E8%99%AB%E5%BC%80%E5%8F%91%E5%AE%9E%E6%88%98_%E5%B4%94%E5%BA%86%E6%89%8D%E8%91%97_2018.04_Pg594.pdf
Reviewed: No
Type: self-study
状态: 告一段落

本书的第2版：

[【2022 年】崔庆才 Python3 网络爬虫学习教程](https://cuiqingcai.com/17777.html)

## 1.8：安装爬虫框架：

### 1.8.1：pyspider爬虫网络框架：

[pyspider安装与初次使用的那些坑_huangzyi的博客-CSDN博客](https://blog.csdn.net/huangzyi/article/details/114289498?ops_request_misc=&request_id=&biz_id=102&utm_term=Could%20not%20create%20web%20server%20li&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-114289498.142^v2^pc_search_result_control_group,143^v4^control&spm=1018.2226.3001.4187)

![Untitled](attachments/Untitled.png)

![Untitled](attachments/Untitled%201.png)

![Untitled](attachments/Untitled%202.png)

![Untitled](attachments/Untitled%203.png)

![Untitled](attachments/Untitled%204.png)

![Untitled](attachments/Untitled%205.png)

![Untitled](attachments/Untitled%206.png)

![Untitled](attachments/Untitled%207.png)

## 4.2 使用Beautiful Soup

Beautiful Soup自动将输入文档转换成Unicode编码，输出文档转换为UTF-8编码。

1. **基本用法：**
    
    首先将HTML字符串传递给BeautifulSoup对象，然后指定解析器的类型，完成BeautifulSoup对象的初始化。
    
    prettify()方法可以将要解析的字符串以标准的缩进格式输出。
    
2. **节点选择器：**
    
    直接调用节点的名称就可以选择节点元素，在调用 *string* 属性就可以得到节点内的文本。适用于单个节点结构层次清晰的HTML文本。
    
    1. **选择元素：**
        
        如 *soup.title* 可以直接写节点名来读取节点以及内部的文本。返回类型全部都是 **bs4.element.Tag** 类型。这种类型有几个有用的属性： *string、name*  等等。当有多个节点名相同时，只会输出第一个。
        
    2. **提取信息**：
        
        获取节点属性的值以及节点名
        
        1. **.name** 即可获取节点的名称
        2. 可以用 **.attrs** 来获取所有的属性。返回值为字典形式。
        3. **.string** 可以获取该节点包含的文本内容。
        4. 嵌套选择，只要soup.title下还有节点，就可以一直嵌套下去
        5. 关联选择：选择一个基准节点。然后在进行上下选择
            1. 子节点和子孙节点
                
                获取直接子节点： **.contents** 或者 **.children**
                
                获取所有子孙节点： **.descendants**
                
            2. 父节点和祖先节点
                
                父节点： **.parent** 
                
                祖先节点： **.parents**
                
            3. 兄弟节点
                
                前/后兄弟节点： **next_sibling**  **previous_sibling**
                
                前/后所有的兄弟节点： **next_siblings**  **previous_siblings**
                
3. **方法选择器**
    
    ***find_all(name, attrs, recursive, text, kwargs)，*** 主要根据 **name** 和 **attrs** 进行查询
    
    在使用 **find_all** 之后，只要还是 **Tag** 类型，那么就可以继续进行嵌套调用。
    
4. **CSS选择器**
    
    使用CSS选择器时，只需要调用 **select()** 方法，传入相应的选择器即可。
    

## 4.3 使用pyquery

1. **初始化**
    
    导入PyQuery包： **from pyquery import PyQuery as pq**
    
    将html文本传入PyQuery对象  **doc = pq(html)**
    
2. **CSS选择器**
- **CSS选择器**
    - **元素选择器**
        - 直接选择文档元素
        - 比如head，p
    - **类选择器**
        - 元素的class属性，比如 `<h1 class="important">`
        - 类名就是important
        - `.important` 选择所有有这个类属性的元素
        - 可以结合元素选择器，比如： `p.important`
    - **ID选择器**
        - 元素的id属性，比如 `<h1 id="intro">`
        - id 就是 intro
        - `#intro` 用于选择id=intro的元素
        - 可以结合元素选择器，比如： `p#intro`
    - **属性选择器**
        - 选择有某个属性的元素，而不论值是什么。
        - `*[title]` 选择所有包含title属性的元素
        - `a[href]` 选择所有带有href的锚元素
        - 还可以选择多个属性，比如： `a[href][title]` ，注意这里要同时满足
        - 限定值： `a[href="www.so.com"]`
    - **后代（包含）选择器**
        - 选择某个元素后代的元素（层级不受限制）
        - 选择h1元素的em元素： `h1 em`
    - **子元素选择器**
        - 范围限制在子元素
        - 选择h1元素的子元素strong： `h1 > strong`
    
    [爬虫之CSS选择器的使用(BeautifulSoup)](https://blog.csdn.net/olizxq/article/details/81838212?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164894868316780264085429%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=164894868316780264085429&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-81838212.142^v5^pc_search_result_control_group,157^v4^control&utm_term=%E7%88%AC%E8%99%AB%E4%B8%AD%E4%BD%BF%E7%94%A8CSS%E9%80%89%E6%8B%A9%E5%99%A8&spm=1018.2226.3001.4187)
    

# 第5章：数据存储

最简单的形式是保存为文本文件：TXT，JSON，CSV等，也可以保存到数据库中

## 5.1 文件存储

主要有TXT，JSON，CSV存储等

### 5.1.1 TXT文本存储、

**优点**：操作简单，兼容任何平台。 **缺点**： 不利于检索。

1. **本节目标**：
    
    保存知乎上“发现”界面的“热门话题”部分，将问题和答案同意保存成文本存储。
    
2. **基本实例**：
    
    用requests将网页源代码获取下来，然后利用pyquery进行解析。将提取的标题、回答者、回答保存到文本
    
    此处利用的时BeautifulSoup进行解析
    
    ```python
    import requests
    from bs4 import BeautifulSoup
    from pyquery import PyQuery as pq
    
    url = "https://www.zhihu.com/explore"
    headers = {
        'User-Agent':"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36",
        'referer':'https://www.zhihu.com/'
    }
    
    response = requests.get(url,headers=headers).text
    # print(response)
    soup = BeautifulSoup(response,'lxml')
    
    # print(soup.prettify())
    items = soup.find_all(attrs={'class':'ExploreCollectionCard-contentItem'})
    print(type(items))
    # print(items)
    file1 = open('a.txt','w',encoding='utf-8')
    for item in items:
        # print(item.find_all(attrs={'class':'ExploreCollectionCard-contentTitle'}))
        # print(type(item.find_all(attrs={'class':'ExploreCollectionCard-contentTitle'})))
        for it in item.find_all(attrs={'class':'ExploreCollectionCard-contentTitle'}):
            title = it.string
        for it in item.find_all(attrs={'class':'ExploreCollectionCard-contentExcerpt'}):
            content = it.string
        # file1.write(title)
        # file1.write('\n')
        # file1.write(content)
        file1.write('\n'.join([title,content]))
        file1.write('\n'+'='*50+'\n')
        # print('\n'+'='*50+'\n')
    ```
    

### 5.1.2 JSON文件存储

JSON，全称为： **JavaScript Object Notation**  JavaScript对象标记，通过对象和数组的组合来表示数据。

1. 对象和数组
    1. **对象**： 使用 { } 包裹起来的内容，数据结构为 {key1：value，key2：value，。。。}的键值对结构
    2. **数组**： 使用 [ ] 包裹起来的内容，
2. 读取JSON
    
    使用python的JSON库来读取JSON文本 ***json.loads()*** 将JSON文本字符串转为JSON对象，***json.dumps()*** 将JSON对象转换为可操作的数据结构，如列表或字典
    

### 5.1.3 CSV文件存储

CSV ，全称为： **Comma-Separated Values** 字符分隔值，比较纯粹，一般只需要用逗号分割全部的数据。

## 5.2 关系型数据库存储

关系型数据库就是基于关系模型的数据库，而关系模型是通过二维表来保存的，所以它的存储方式就是行列组成的表，每一列就是一个字段，每一行是一条记录。表可以看作某个实体的集合，而实体之间存在联系，这就需要表与表之间的关联关系来体现。

关系型数据库有：SQLite、MySQL、Oracle、SQL Server、DB2

### 5.2.1 MySQL的存储

1. **链接数据库**
2. **创建表**
3. **插入数据**
4. **更新数据**
5. **删除数据**
6. **查询数据**

## 5.3 非关系型数据库存储

NoSQL，全称为： **Not Only SQL** 意为不仅仅是SQL，泛指非关系型数据库。NoSQL是基于键值对的，而且不需要经过SQL层的解析。

### 5.3.1 MongoDB存储

1. **链接MongoDB**
2. **指定数据库**
3. **指定集合**
4. **插入数据**
5. **查询**
6. **计数**
7. **排序**
8. **偏移**
9. **更新**
10. **删除**
11. **其他操作**

### 5.3.2 Redis存储

1. **Redis和StrictRedis**
    
    Redis是StrictRedis的子类，这里推荐使用StrictRedis
    
2. **连接Redis**
    
    ```python
    from redis import StrictRedis,ConnectionPool
    
    redis = StrictRedis(host='localhost',port=6379,db=0)
    redis.set('name','Bob')
    print(redis.get('name'))
    
    # pool = ConnectionPool(host = 'localhost',port = 6379,db=0)
    # redis = StrictRedis(connection_pool=pool)
    ```
    

# 第6章：Ajax数据爬取

由于 **requests** 获取的都是原始的HTML文档，而浏览器则是经过 ***JavaScript*** 处理数据后生成的结果。这些数据可能通过 **Ajax** 加载，也可能包含在 **HTML** 文档中。

## 6.1：什么是Ajax

**Ajax** 全称： **Asynchronous JavaScript and XML** 即异步的JavaScript和XML。利用 **JavaScript** 在保证页面不被刷新、页面链接不改变的情况下和服务器交换数据并更新部分网页。

1. **基本原理**
    
    发送 **Ajax** 请求到网页更新的这个过程可以分为以下3步：
    
    1. **发送请求**
        
        ```jsx
        var xmlhttp;
        if (window.XMLHttpRequest){
        		//code for IE7+,firefox,Chrome,Opera, Safari
        		xmlhttp = new XMLHttpRequest();
        }else{//code for IE6,IE5
        		xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
        }
        xmlhttp.onreadystatechange=function(){
        		if (xmlhttp.readyState==4 && xmlhttp.status ==200){
        				document.getElementById("myDiv").innerTML=xmlhttp.responseText;
        		}
        }
        xmlhttp.open("POST","/ajax/",true);
        xmlhttp.send();
        ```
        
        实际上是新建了 **XMLHttpRequest** 对象，然后调用 **onreadystatechange**  属性设置了监听，然后调用 **open()** 和 **sned()** 方法向某个链接发送了请求。
        
    2. **解析内容**
    3. **渲染网页**
        
        **JavaScript** 有改变网页内容的能力
        
    
    真实的数据其实都是一次次的 **Ajax** 请求，只需要知道这些请求是怎么发送的，发往哪里，发了哪些参数。就可以利用Python来模拟这个发送操作。
    

## 6.2：Ajax分析方法

1. **查看请求**
    
    利用开发者工具，打开到 **NewWork** 界面，如果一个请求为***X-Requested-With: XMLHttpRequest*** 的话，那么这个请求就是 **Ajax** 请求。
    
2. **过滤请求**
    
    在开发者工具上方的筛选栏点击 **XHR** 即可选出所有的 ***Ajax*** 请求。了解了 **Request URL 、Request Headers、REsponse Headers。**就很容易模拟请求
    

## 6.3:Ajax结果提取

模拟 **Ajax** 请求，爬取微博页面

1. **分析请求**
    
    每个 **Ajax** 请求都有几个固定的参数不变，而仅仅只有一个参数改变，在微博中是 **since_id** 在改变
    
2. **分析响应**
    
    动态 **Ajax** 页面主要找出规律，找到网页中不变的部分以及变的部分，并找出变化部分的变化规律，然后以此构建字典，并使用 **urllib.parse** 中的 **urldecode** 方法，将不变的部分和字典中的数据构建为一个完整的 **URL。**然后再次请求即可。
    
3. **实战演练**

```jsx
"""主要提取微博特定账号所发的所有微博动态"""
import requests
from urllib.parse import urlencode
from pyquery import PyQuery as pq
# 初始URL
url = 'https://m.weibo.cn/api/container/getIndex?uid=2830678474&t=0&luicode=10000011&lfid=100103type%3D1%26q%3D%E5%B4%94%E5%BA%86%E6%89%8D&containerid=1076032830678474'
# 请求头信息
headers = {
    "Referer":'https://m.weibo.cn/u/2830678474',
    'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36',
    'X-Requested-With': 'XMLHttpRequest',
    'Host':'m.weibo.cn'
}

"""一个返回since_id的函数"""
def return_Since_id(Previous_url):   # 参数为上一个 Ajax 类型的url
    since_id_response = requests.get(Previous_url,headers=headers)
    since_id_items = since_id_response.json()
    return since_id_items.get('data').get('cardlistInfo')['since_id']

since_id = 4746605166595404      # 初始查找页面
base_url = 'https://m.weibo.cn/api/container/getIndex?'  #固定url部分

file = open('webo.txt','w',encoding='utf-8')
while since_id > 4630000000000000:
    since_id = return_Since_id(url)
    params = {
        'uid':'2830678474',
        't':'0',
        'luicode':'10000011',
        'lfid':'100103type%3D1%26q%3D%E5%B4%94%E5%BA%86%E6%89%8D',
        'containerid':'1076032830678474',
        'since_id':str(since_id)   # 这里填写一个since_id = return_Since_id(Previous_url)
    }
    url = base_url+urlencode(params)   
    response = requests.get(url,headers=headers)
    json1 = response.json()      # 观察返回值的特征，json文本会更容易观察
    if json1:  
        items = json1.get('data').get('cards')
        for item in items:
            item = item.get('mblog')
            id = 'id:'+item.get('id')
            text = 'text：'+pq(item.get('text')).text()
            attitudes="attitudes："+ str(item.get('comments_count'))
            reposts = 'reposts：'+str(item.get('reposts_count'))
            file.write('\n'.join([id,text,attitudes,reposts]))
            file.write('\n'+'='*50+'\n')
```

在不知道该类内有什么方法时，可以使用 **type()** 函数，查看返回值的类型，然后在命令行之中查看type() 返回的值的使用方法。

如果是 **Ajax** 网页，一般情况可以先写一个爬取一张网页的函数，然后再写一个获取后续网页的函数，最后在主函数中组合使用即可。

# 第7章：动态渲染页面爬取

动态渲染：页面由 **JavaScript**  生成，并非原始的**HTML**代码，要获取这些页面的数据，可以直接使用模拟浏览器运行的方式来实现，这样就可以做到在浏览器中看到的是什么样，抓取到的源代码就是什么样。

**Python** 提供了很多模拟浏览器运行的库，比如 **Selenium、Splash、PyV8、Ghost**等等。

## 7.1 Selenium的使用

**Seklenium: 自动化测试工具；可以驱使浏览器执行特定的动作，**如点击、下拉等操作。同时可以获取浏览器当前呈现的页面的源代码、做到可见即可爬。

1. **基本使用**

```jsx
"""Selenium的基本用法"""
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.wait import WebDriverWait

browser = webdriver.Chrome()

try:
    browser.get('https://www.baidu.com')
    input = browser.find_element_by_id('kw')
    input.send_keys('Python')
    input.send_keys(Keys.ENTER)
    wait = WebDriverWait(browser,10)
    wait.until(EC.presence_of_element_located((By.ID,'content_left')))
    print(browser.current_url)
    print(browser.get_cookies())
    print(browser.page_source)
finally:
    browser.close()
```

运行代码之后，会自动调出Chrome浏览器，然后搜索 **Python** ，接着转到搜索结果页，搜索结果加载出来之后，控制台会分别输出当前的 **URL、当前的Cookies 和网页源代码** 。 

1. **声明浏览器对象**
    
    ```jsx
    from selenium import webdriver
    
    browser = webdriver.Chrome()
    browser = webdriver.Firefox()
    browser = webdriver.Edge()
    ```
    
    selenium不仅支持很多PC端浏览器，还支持 **Android** 等手机端的浏览器。，在声明浏览器对象之后，就是调用 **browser** 模拟浏览器的各种操作。
    
2. **访问页面**
    
    利用 ***get()*** 方法来请求网页，参数传入链接URL即可。
    
3. **查找节点**
    
    用于查找输入框或者表单的位置
    
    - **单个节点**
        
        ***find_element_by_name()*** 通过 **name** 值获取；
        
        ***find_element_by_id()*** 通过 **id** 获取；
        
        还可以根据 **XPath、CSS选择器** 等获取方式获取。
        
    
    ```python
    """三种获取方式"""
    input_first = browser.find_element_by_id('q')
    input_second = browser.find_element_by_css_selector('#q')
    input_third = browser.find_element_by_xpath('//*[@id="q"]')
    print(input_first,input_second,input_third)
    ```
    
     获取单个节点的所有方法：
    
    ```python
    """在命令行中的python环境中导入webdriver,"""
    from selenium import webdriver
    
    # 可查看这个类里面的所有方法，包括获取单个节点的方法。
    dir(selenium.webdriver.chrome.webdriver.WebDriver)
    
    ```
    
    此外，还有 ***find_element(by,value)*** 传入查找方式和值即可，等价于上述方式。
    
    - **多个节点**
        
        ***find_elements(by,value)*** 方法，
        
        返回值都是 **WebElement** 类型。
        
    
    ```python
    # 查看淘宝网页左侧的所有项目
    lis = browser.find_elements_by_css_selector('.service-bd li')
    print(lis)
    ```
    
4. **节点交互**
    
    模拟浏览器执行一些操作，比较常见的有：
    
    ***send_keys()*** 输入文字。
    
    ***clear()*** 清空文字
    
    ***click()*** 点击按钮
    
    基本上的操作就是，先找到输入框的节点，然后调用 send 方法输入参数，再找到搜索按钮的节点，调用 click 方法进行搜索。
    
    ```python
    # 节点交互，控制浏览器进行输入等操作
    input_first.send_keys('iphone')
    time.sleep(1)
    input_first.clear()
    input_first.send_keys('ipad')
    button = browser.find_element_by_class_name('btn-search')
    button.click()
    ```
    
    [7. WebDriver API - Selenium Python Bindings 2 documentation](https://selenium-python.readthedocs.io/api.html#module-selenium.webdriver.remote.webelement)
    
5. **动作链**
    
    **动作链**： 用于模拟鼠标拖拽、键盘按键等操作
    
    首先打开网页中的一个拖拽实例，然后依次选中要拖拽的节点和拖拽到的目标节点，然后声明 **ActionChains** 对象，然后通过调用 actions 的 **drag_and _drop()** 方法，再调用 **perfrom()** 方法。
    

```python
from selenium.webdriver import ActionChains
url = 'http://www.runoob.com/try/try.php?filename-jqueryui-api-droppable'
browser.switch_to.frame('iframeResult')
source = browser.find_element_by_css_selector('#draggable')
target = browser.find_elements_by_css_selector('#dropable')
actions = ActionChains(browser)
actions.drag_and_drop(source,target)
actions.perform()
```

[7. WebDriver API - Selenium Python Bindings 2 documentation](https://selenium-python.readthedocs.io/api.html#module-selenium.webdriver.common.action_chains)

1. **执行Javascript**
    
    使用 ***execute_script()*** 方法实现 **JavaScript** 的下拉进度条操作
    
    需要结合 **Javascript** 的一些操作写法，比如需要了解 **JavaScript** 的一些对象名称以及一些基本的知识。
    

```python
browser.get('https://www.zhihu.com/explore')
browser.execute_script('window.scrollTo(0,document.body.scrollHeight)')
browser.execute_script('alert("To Bottom')
```

[一文教你掌握JavaScript基本操作（详解）_王涛涛.的博客-CSDN博客_js的基本操作](https://blog.csdn.net/WangTaoTao_/article/details/98186679?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164881425416782246442929%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=164881425416782246442929&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-98186679.142^v5^pc_search_result_control_group,157^v4^control&utm_term=javascript%E6%93%8D%E4%BD%9C&spm=1018.2226.3001.4187)

1. **获取节点信息**
    
    两种方法：
    
    - 通过 **page_source** 获取网页的源代码，然后通过解析库，如 **BeautifulSoup** 来提取信息。
    - 使用 **selenium** 提供的相关方法来直接提取节点信息。 注：其返回值类型是： **WebElement**
    1. **获取属性**
        
        ***get_attribute()*** 方法用于获取节点的属性，但是必须选中这个节点。
        
        ```python
        # 获取节点属性
        browser = webdriver.Chrome()
        browser.get('https://www.zhihu.com/explore')
        logo = browser.find_element_by_id('zh-top-link-logo')
        print(logo)
        print(logo.get_attribute("class"))
        ```
        
    2. **获取文本值**
        
        ***text*** 属性：获取节点内部的文本信息，相当于 **BeautifulSoup** 的 **get_text()** 方法。
        
    3. **获取id、位置、标签名和大小**
        
        ***id*** : 获取节点 id
        
        ***location*** ：获取该节点在页面中的相对位置
        
        ***tag_name*** ：获取标签名称
        
        ***size*** ：获取节点的大小，也就是宽高。
        
    
    ```python
    input = browser.find_element_by_class_name('css-1hlrcxk')
    print(input.id)
    print(input.location)
    print(input.tag_name)
    print(input.size)
    ```
    
2. **切换框架**
    
    **iframe** ：为子 **Frame，** 相当于页面的子页面。**selenium** 在打开页面时，默认打开的是父级 **Frame ，**如果此时页面还有子 **Frame** ，它是不能获取到子 **Frame** 里面的节点的。
    
    ***switch_to.frame()*** ：用来切换Frame
    
3. **延时等待**
    
    由于 ***get()*** 方法会在网页框架加载结束之后结束执行，如果此时网页没有完全加载，或者网页中还有 **Ajax** 请求，那么我们获取到的源代码就不是完整的。所以需要等待一段时间，来让所有节点全部加载完成。
    
    两种方法：
    
    - **隐式等待**
        
        当查找节点没有立即出现的时候，隐式等待等待一段时间后在查找DOM，默认时间为0. 
        
        ***implicitly_wait()*** 方法实现隐式等待
        
        ```python
        browser.implicitly_wait(10)
        browser.get('https://www.zhihu.com/explore')
        input = browser.find_element_by_class_name('zu-top-add-question')
        print(input)
        ```
        
    - **显式等待**
        
        隐式等待只能固定一个时间，时间到了之后网页就会关闭，不论有没有加载完成。
        
        而显式等待则是指定查找的节点，然后指定一个最长的等待时间，如果在规定时间内加载出来了这个节点，则返回查找的节点，如果超过规定时间还没加载出来，则抛出超时异常。
        
        ```python
        browser = webdriver.Chrome()
        browser.get('https://www.taobao.com/')
        wait = WebDriverWait(browser,10)
        input = wait.until(EC.presence_of_element_located((By.ID,'q')))
        button = wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR,'.btn-search')))
        print(input,button)
        ```
        
        首先引入 **WenDriverWait** 这个对象，指定最长等待时间，然后调用 **until** 方法，并传入要等待条件 **excepted_conditions** 比如 **presence_of_element_located** 如果节点出现，则返回，如果没出现则抛出异常。
        
        ![Untitled](attachments/Untitled%208.png)
        
        ![Untitled](attachments/Untitled%209.png)
        
4. **前进和后退**
    
    ***back()*** ：使浏览器后退
    
    ***forward()*** ：使浏览器前进
    
    ```python
    # 控制浏览器前进和后退
    browser = webdriver.Chrome()
    browser.get('https://www.baidu.com/')
    browser.get('https://www.taobao.com/')
    browser.get("https://www.python.org/")
    browser.back()
    time.sleep(2)
    browser.forward()
    browser.close()
    ```
    
5. **Cookies**
    
    获取、添加、删除Cookies：
    
    ```python
    browser = webdriver.Chrome()
    browser .get('https://www.zhihu.com/explore')
    print(browser.get_cookies())
    browser.add_cookie({'name':'name','domain':'www.zhihu.com','value':'germey'})
    print(browser.get_cookies())
    browser.delete_all_cookies()
    print(browser.get_cookies())
    ```
    
6. **选项卡管理**
    
    Selenium也可以读选项卡进行操作
    
    ```python
    import time
    browser = webdriver.Chrome()
    browser.get('https://www.baidu.com')
    browser.execute_script('window.open()')   # window_open() 新开启一个选项卡
    print(browser.window_handles)  # window_handles: 获取当前打开的所有选项卡
    browser.switch_to_window(browser.window_handles[1])
    browser.get('https://www.taobao.com')
    time.sleep(2)
    browser.switch_to_window(browser.window_handles[0])
    browser.get('https://www.python.org')
    ```
    
7. **异常处理**
    
    操作过程中会遇到超时、节点未找到等错误，一旦出现这些错误，程序便不会继续运行了。可以使用 ***try except*** 语句来捕获各种异常。
    
    ```python
    from selenium.common.exceptions import TimeoutException,NoSuchElementException
    
    browser = webdriver.Chrome()
    try:
        browser.get('https://www.baidu.com')
    except TimeoutException:
        print("Time Out!")
    try:
        browser.find_element_by_id('hello')
    except NoSuchElementException:
        print('No Element')
    finally:
        browser.close()
    ```
    
    [7. WebDriver API - Selenium Python Bindings 2 documentation](https://selenium-python.readthedocs.io/api.html#module-selenium.common.exceptions)
    

## 7.2 Splash的使用

**Splash** 是一个 **JavaScript** 渲染服务，是一个带有 HTTP API 的轻量级浏览器，同时它对接了 Python 中的 **Twisted** 和 **QT** 库，同样可以利用它来实现动态渲染页面的抓取。

1. **功能介绍**
    - 异步方式处理多个网页渲染过程
    - 获取渲染后的页面的源代码或截图
    - 通过关闭图片渲染或使用 **Adblock** 规则来加快页面渲染的速度
    - 可执行特定的 **JavaScript** 脚本
    - 可通过 **Lua** 脚本来控制页面渲染过程
    - 获取渲染的详细过程并通过 **HAR** ***(HTTP Archive)*** 格式呈现
2. **实例引入**
    
    在命令行端运行了 `docker run -p 8050:8050 scrapinghub/splash` 启动 **splash** 服务，然后在浏览器中搜索 `[localhost:8050](http://localhost:8050)` ，即可进入 **splash**。里面的脚本主要是由 **Lua** 语言编写的：主函数为：
    
    ```lua
    function main(splash, args)
      assert(splash:go(args.url))
      assert(splash:wait(0.5))
      return {
        html = splash:html(),
        png = splash:png(),
        har = splash:har(),
      }
    end
    ```
    
    其中返回值分别有：网页的源代码、截图以及HAR信息。
    
    A HAR file is an **archive saved in the HTTP Archive**(HAR) format, which is a JSON -formatted format used to save collected HTTP performance data. It contains information about webpages a web browser has loaded, which includes the tracked webpages, response times, and web browser version.
    HAR 文件是以 HTTP 存档 (HAR) 格式保存的存档，该格式是一种 JSON 格式的格式，用于保存收集的 HTTP 性能数据。 它包含有关 Web 浏览器已加载的网页的信息，其中包括跟踪的网页、响应时间和 Web 浏览器版本。
    
    使用 **Lua脚本** 来控制页面的加载过程，加载过程完全模拟浏览器，最后返回各种格式的结果。如网页源代码和截图。
    
3. **Splash Lua 脚本**
    
    ***Lua脚本的基本语法***：
    
    [Lua 基本语法](https://www.runoob.com/lua/lua-basic-syntax.html)
    
    Splash 可以通过 **Lua** 脚本执行一系列的渲染操作，这样就可以使用 Splash 来模拟类似 Chrome、PhantomJS 的操作了
    
    - **入口及返回值**
        
        **Lua** 脚本固定以 **main()** 为执行函数，每次都要声明 **splash:** 然后后面再写操作，其中 **evaljs()** 会执行 **JavaScript** 脚本。 **return** 会返回后面的值，可以返回字典，也可以返回字符串内容。
        
        **local** 用于声明变量
        
        ```lua
        function main(splash,args)
          splash:go("https://www.baidu.com")
          splash:wait(0.5)
          local title = splash:evaljs("document.title")
          return {title=title}
        end
        ```
        
    - **异步处理**
        
        **Splash** 支持异步处理，但是没有明显的回调方法，其回调的跳转是在 **Splash** 内部完成的。主要是其 **wait()** 方法。相当于 Python 中的 **sleep()** 方法， **Splash** 执行到这个方法时，会转而去执行其他任务，然后在指定的时间过后再回来继续处理。而且 **Splash** 中的拼接操作符为 `..` 
        
        ```lua
        function main(splash,args)
          local example_urls = {"www.baidu.com","www.taobao.com","www.zhihu.com"}
          local urls = args.urls or example_urls
          local results = {}
          for index ,url in ipairs(urls) do
            local ok,reason = splash:go("https://" .. url)
            if ok then
              splash:wait(2)
              results[url] = splash:png()
            end
          end
          return results
        end
        ```
        
4. **Splash对象属性**
    - 各种属性：
        
        **main()** 方法的第一个参数就是 **splash**， 这相当于 **Selenium** 中的 **webdriver** 对象，可以调用它的一些属性和方法来控制加载进程。
        
        - **args**
            
            用于获取加载时配置的参数，比如 URL， 如果是 GET 请求，它还可以获取 GET 请求参数；如果是 POST 请求，它可以获取表单提交的数据。 **Splash** 支持第二个参数为 **args**
            
            ```lua
            function main(splash,args)
            	local url = args.url
            end
            
            # 以上代码等同于：
            function main(splash)
            	local url = splash.args.url
            end
            ```
            
        - **js_enabled**
            
            这是 **Splash** 执行 **JavaScript** 脚本的开关，可以自己选择是否执行 **JavaScript** 脚本。
            
            ```lua
            function main(splash,args)
            	splash.js_enabled = false
            	splash:go("https://www.baidu.com")
            	local title = splash:evaljs("docunment.title")
            	return {title=title}
            end
            ```
            
            此时执行 **evaljs** 就会报错，因为已经将 **js_enabled** 设为了 **false**
            
        - **resource_timeout**
            
            超时检测，如果设为 `0` 或者 `nil`  *（类似于python中的None）* ，代表不检测，否则在超时之后会报错。
            
            ```lua
            function main(splash,args)
            	splash.resource_timeout = 0.1
            	splash:go("https://www.baidu.com")
            	return splash:png()
            end
            ```
            
            此属性适合在网页加载速度比较慢的情况下设置。
            
        - **image_enabled**
            
            配置网页图片是否加载，但是禁用图片加载可能会影响 **JavaScript** 的渲染。
            
            ```lua
            function main(splash.args)
            	splash.image_enabled = false
            	assert(splash:go("https://www.jd.com"))
            	return {png=splash:png()}
            end
            ```
            
            同一行适应于网页加载速度比较慢的情况
            
        - **plugins_enabled**
            
            用于控制浏览器插件是否开启：
            
            `splash.plugins_enabled=true/false`
            
        - **scroll_position**
            
            控制页面上下火左右滚动： `splash.scroll_position = {y=400}` 
            
            这个操作是控制网页向下滚动400像素值。
            
5. **Splash对象的方法**
    - 各种方法：
        - **go()**
            
            用来请求链接，并且是可以模拟 GET 和 POST 请求的，支持传入表头、表单等数据
            
            `ok, reason = splash:go(url,baseurl=nil, headers=nil, http_method = "GET", body=nil, formdata=nil}`
            
        - **wait()**
            
            用于控制页面的等待时间：
            
            `ok,reason = splash:wait(time, cancel_on_redirect=false, cancel_on_error=true}`
            
        - **jsfunc()**
            
            可以直接调用 **JavaScript** 定义的方法，相当于实现了 **JavaScript** 方法到 **Lua脚本** 的转换，所调用的方法需要用 双中括号 包围。
            
        - **evaljs()**
            
            用于执行 **JavaScript** 代码并返回最后一条 **JavaScript** 语句的返回结果： `result = splash:evaljs(js)` 
            
        - **runjs()**
            
            与 **evaljs()** 方法类似。
            
        
        除了这些，还有很多方法。
        
6. **Splash API 调用**
    
    将 **Splash** 与 **Python** 程序结合
    
    - **render.html**
        
        此接口用于获取 **JavaScript** 渲染的页面的HTML代码，接口地址就是 Splash 的运行地址加此接口名称，例如： `[http://localhost:8050/render.html](http://localhost:8050/render.html)` 
        
        [Splash HTTP API - Splash 3.5 documentation](https://splash.readthedocs.io/en/stable/api.html#render-html)
        
    - **render.png, render.har, render.json**
        
        [Splash HTTP API - Splash 3.5 documentation](https://splash.readthedocs.io/en/stable/api.html#render-png)
        

## 7.3 Splash负载均衡配置

这篇文章其实就是搬运这本书上的所有内容的：

[Splash 负载均衡配置_五层楼的博客-CSDN博客_splash负载均衡](https://blog.csdn.net/qq_33891000/article/details/120614262?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164905105816780357234325%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=164905105816780357234325&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-120614262.142^v5^pc_search_result_control_group,157^v4^control&utm_term=splash%E8%B4%9F%E8%BD%BD%E5%9D%87%E8%A1%A1%E9%85%8D%E7%BD%AE&spm=1018.2226.3001.4187)

## 7.4 使用Selenium爬取淘宝商品

对于有些即使用 **Ajax** 加载的网页，但其中可能会包含有加密密钥，因此，自己构造 **Ajax** 可能并不理想。所以使用 **Selenium** 爬取这些网页会更合适。

1. **本节目标**
    
    利用 **Selenium** 爬取淘宝商品并用 **Pyquery** 解析得到的商品的图片、名称、价格、购买人数、商铺名称和商铺所在地信息，并将其保存到  **MongoDB**。
    
2. **准备工作**
    
    需要：Chrome、ChromeDriver。
    
3. **接口分析**

最重要的一点，自己写的时候被一对括号卡了半天，返回值里面的，return 函数后面那个不能加括号 `return total.text` 。谨记 

- 自己写的代码：
    
    ```python
    import time
    
    import pymongo
    from selenium import webdriver
    from selenium.webdriver.common.by import By
    from selenium.webdriver.support.wait import WebDriverWait
    from selenium.webdriver.support import expected_conditions as EC
    from selenium.common.exceptions import TimeoutException
    from pyquery import PyQuery as pq
    
    options = webdriver.ChromeOptions()
    options.add_argument('--disable-blink-features=AutomationControlled')
    browser = webdriver.Chrome(options=options)
    browser.maximize_window()
    # browser.get('https://www.taobao.com/')
    wait = WebDriverWait(browser, 10)
    
    KEYWORD = '键盘'
    
    def search_products():
        print('正在搜索...')
        try:
            browser.get('https://www.taobao.com')
            input_key = wait.until(EC.presence_of_element_located((By.CSS_SELECTOR, '.search-bd .search-suggest-combobox input')))
            button = wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, '.search-bd .search-button button')))
            input_key.clear()
            input_key.send_keys(KEYWORD)
            button.click()
            total = wait.until(EC.presence_of_element_located((By.CSS_SELECTOR, '#mainsrp-pager .total')))
            # get_products()
            return total.text
        except TimeoutException:
            print('搜索出错')
            return search_products()
    
    def get_next_page(page_num):
        print('正在翻页:',page_num)
        try:
            input = wait.until(EC.presence_of_element_located((By.CSS_SELECTOR, '#mainsrp-pager input')))
            submit = wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, '#mainsrp-pager .btn')))
            input.clear()
            input.send_keys(page_num)
            submit.click()
            # wait.until(EC.text_to_be_present_in_element((By.CSS_SELECTOR, '#mainsrp-pager li.item.active > span'),str(page_num)))
            get_products()
        except TimeoutException:
            get_next_page(page_num)
    
    def get_products():
        wait.until(EC.presence_of_element_located((By.CSS_SELECTOR, '#mainsrp-itemlist .m-itemlist .items .item')))
        html = browser.page_source
        doc = pq(html)
        items = doc('#mainsrp-itemlist .m-itemlist .items .item').items()
        for item in items:
            products = {
                'img': item.find('.pic img').attr('data-src'),
                'price': item.find('.ctx-box .row-1 .price').text(),
                'deal': item.find('.ctx-box .deal-cnt').text(),
                'title': item.find(".title").text(),
                'shop': item.find('.ctx-box .row-3 .shop').text(),
                'location': item.find('.ctx-box .location').text()
            }
            # print(products)
            save_to_mongo(products)
    
    MONGO_URL = 'localhost'
    MONGO_DB = 'taobao'
    MONGO_COLLECTION = 'jianpan'
    
    client = pymongo.MongoClient(MONGO_URL)
    db = client[MONGO_DB]
    
    def save_to_mongo(result):
        try:
            if db[MONGO_COLLECTION].insert_one(result):
                print('存储成功:\n', result)
        except Exception:
            print('存储失败:\n', result)
    
    MAX_PAGES = 4
    
    def main():
        try:
            search_products()
            for i in range(1, MAX_PAGES + 1):
                time.sleep(3)
                get_next_page(i)
        except Exception:
            print("爬取失败")
        finally:
            browser.close()
    
    if __name__ == '__main__':
        main()
    ```
    
1. **浏览器的无头模式**
    
    ```python
    options = webdriver.ChromeOptions()
    options.add_argument('--headless')
    browser = webdriver.Chrome(options=options)
    ```
    
2. **对接 Firefox**
    
    `browser = webdriver.Firefox()`
    
3. **对接 PhantomJS**
    
    **PhantomJS** 同样是一个无界面浏览器，在抓取时，同样不会弹出窗口
    
    `browser = webdriver.PhantomJS()`
    
    此外，它还支持命令行配置，比如可以设置缓存和禁用图片加载的功能，进一步提高爬取效率
    
    `SERVICE_ARGS = ['--load images=false','--disk-cache=true']`
    
    `browser = webdriver.PhantomJS(service_args = SERVICE_ARGS)`
    

# 第8章：验证码的识别

反爬机制之一：设置验证码，本章主要涉及以下验证码： **普通图形验证码，极验滑动验证码，点触验证码，微博宫格验证码**

## 8.1 图形验证码的识别

1. **本节目标**
    
    以之王的验证码为例，学习利用 **OCR** 技术来识别图形验证码。
    
2. **识别测试**
    
    ```python
    import tesserocr
    from PIL import Image
    
    image = Image.open('验证码图片/code.jpg')
    result = tesserocr.image_to_text(image)
    print(result)
    ```
    
3. **验证码处理**
    
    当验证码图片中包含很多无关线条时， **OCR** 识别可能会出错，这时，就需要首先对验证码图片进行预处理，比如转为灰度图，二值化操作等等。
    
    利用 **Image** 对象的 **convert()** 方法传入参数可以改变图像：
    
    ***L：*** 转为灰度图： `image = image.convert(”L””)`
    
    ***1:***   转为二值图： `image = image.convert("1")`
    
    在从 **PIL** 包导入 **Image** ，并且使用 **open()** 方法之后，返回的值的类型为 ***PIL.Image.Image*** 类型，可以在命令行中查看所有的方法。
    
    此外还可以指定二值化的阈值：
    
    ```python
    image = image.convert("L")
    threshold = 80
    table = []
    for i in range(256):
        if i < threshold:
            table.append(0)
        else:
            table.append(1)
    image = image.point(table,'1')
    image.show()
    result = tesserocr.image_to_text(image)
    print(result)
    ```
    
    这里的阈值 **threshold** 需要看情况自己决定是多少，太大或者太小都会影响图片的处理。
    

## 8.2 极验滑动验证码的识别

1. **了解极验验证码**
    
    拖动滑块拼合图像，如果图像完全拼合，则验证成功，即表单成功提交，否则需要重新验证。
    
2. 识别思路
    
    如果直接模拟表单提交，会比较难构造加密参数，需要分析其加密和校验逻辑，相对繁琐，所以可以直接模拟浏览器动作的方式来完成验证。可以直接使用 **Selenium** 进行模拟
    
    识别验证需要三步：
    
    1. 模拟点击验证按钮
    2. 识别滑动缺口的位置
    3. 模拟拖动滑块
    
    第（1）步识别比较简单：直接使用 **Selenium** 模拟点击按钮
    
    第（2）步：识别缺口位置：
    利用图像处理的相关方法，首先观察缺口的位置，缺口周围边缘有明显的断裂边缘，边缘和边缘周围有明显的区别，所以可以实现一个边缘检测算法来确定缺口的位置。可以利用和原图对比检测的方式来识别缺口的位置，因为在没有滑动之前，缺口并没有呈现。
    
    第（3）步：由于极验验证码设置了机器轨迹识别，匀速移动，随即速度移动等方法都不能通过验证，只有模拟人的先加速后减速，才能模拟成功。
    
3. **初始化**
    
    这是一个自己修改过的版本，主要修改的地方是：由于第三版的滑动验证码在一开始的时候已经不会出现完整的图片了，因此，这里使用了 **opencv** 来获取缺口位置。
    
    - 完整代码：
        
        ```python
        import time
        import requests
        from selenium import webdriver
        from selenium.webdriver.support.wait import WebDriverWait
        from selenium.webdriver.support import expected_conditions as EC
        from selenium.webdriver.common.by import By
        from selenium.webdriver.common.action_chains import ActionChains
        import re
        import cv2
        
        # selenium 对象的初始化：
        PHONE = 15927125361
        PASSWORD = 'hero934.'
        
        class CrackGeetest():
            def __init__(self):
                self.url = 'https://account.geetest.com/login'
                self.browser = webdriver.Chrome()
                self.wait = WebDriverWait(self.browser, 20)
                self.phone = PHONE
                self.password = PASSWORD
        
            # 模拟点击：首先获取点击验证的按钮：
            def get_verify_button(self):
                """
                获取初始验证按钮
                :param self: 按钮对象
                :return:
                """
                button = self.wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, '.geetest_btn_click')))
                return button
        
            def get_bj_image(self):
                bj_image = self.wait.until(EC.presence_of_element_located((By.CSS_SELECTOR, '.geetest_bg')))
                url_str = bj_image.get_attribute('style')
                img_url = re.search("https:.*?png", url_str).group()
                html = requests.get(img_url)
                with open("bj_image.png", 'wb') as f:
                    f.write(html.content)
        
            def get_qk_image(self):
                bj_image = self.wait.until(EC.presence_of_element_located((By.CSS_SELECTOR, '.geetest_slice_bg')))
                url_str = bj_image.get_attribute('style')
                img_url = re.search("https:.*?png", url_str).group()
                html = requests.get(img_url)
                with open("qk_image.png", 'wb') as f:
                    f.write(html.content)
        
            def find_location(self, bj_image, qk_image):
                bj_img = cv2.imread(bj_image)
                qk_img = cv2.imread(qk_image)
                bj_img_edge = cv2.Canny(bj_img, 200, 350)
                qk_img_edge = cv2.Canny(qk_img, 300, 400)
                bj_img_rgb = cv2.cvtColor(bj_img_edge, cv2.COLOR_GRAY2RGB)
                qk_img_rgb = cv2.cvtColor(qk_img_edge, cv2.COLOR_GRAY2RGB)
                result = cv2.matchTemplate(qk_img_rgb, bj_img_rgb, cv2.TM_CCOEFF_NORMED)
                min_val, max_val, min_loc, max_loc = cv2.minMaxLoc(result)
                x = max_loc[0]
                th, tw = qk_img_rgb.shape[:2]
                tl = max_loc
                br = (tl[0] + tw, tl[1] + th)
                return tl, br
        
            def get_track(self, distance):
                """
                根据偏移量获取移动轨迹
                :param distance: 偏移量
                :return: 移动轨迹
                """
                track = []  # 移动轨迹
                current = 0  # 当前位移：
                mid = distance * 4 / 5  # 减速阈值：
                t = 0.2  # 计算间隔
                v = 0  # 初速度
                while current < distance:
                    if current < mid:
                        a = 2  # 加速度为+2
                    else:
                        a = -3  # 加速度为-3
                    v0 = v  # 初速度为v0
                    v = v0 + a * t  # 当前速度
                    move = v0 * t + (1 / 2) * a * t * t  # 移动距离
                    current += move  # 当前位移
                    track.append(round(move))
                return track
        
            def move_to_gap(self, slider, tracks):
                """
                拖动滑块到缺口处
                :param slider: 滑块
                :param tracks: 轨迹
                :return:
                """
                ActionChains(self.browser).click_and_hold(slider).perform()
                for x in tracks:
                    ActionChains(self.browser).move_by_offset(xoffset=x, yoffset=0).perform()
                time.sleep(0.5)
                ActionChains(self.browser).release().perform()
        
        test_geetest = CrackGeetest()
        test_geetest.browser.get(test_geetest.url)
        #
        # # 用户名输入节点查找以及输入
        # phone_input = test_geetest.wait.until(EC.presence_of_element_located((By.CSS_SELECTOR, 'input[type="text"]')))
        # phone_input.send_keys(test_geetest.phone)
        #
        # # 密码输入节点查找以及输入
        # password_input = test_geetest.wait.until(EC.presence_of_element_located((By.CSS_SELECTOR, "input[type='password']")))
        # password_input.send_keys(test_geetest.password)
        #
        # # 点击验证按钮
        veryfy_button = test_geetest.get_verify_button()
        veryfy_button.click()
        
        test_geetest.get_bj_image()
        test_geetest.get_qk_image()
        
        bj_image = "bj_image.png"
        qk_image = "qk_image.png"
        
        distance = test_geetest.find_location(bj_image, qk_image)
        distance = distance[0][0]
        
        tracks = test_geetest.get_track(distance)
        print(tracks)
        slider = test_geetest.wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, '.geetest_btn')))
        
        test_geetest.move_to_gap(slider,tracks)
        ```
        
4. **结语**
    
    本节的关键在于识别的思路，如何识别缺口的位置、生成运动轨迹等。其中识别缺口位置，本版本主要通过 **opencv** 来实现，主要依赖其中的两个函数：`matchTemplate(qk_img_rgb, bj_img_rgb, cv2.TM_CCOEFF_NORMED)` ，`cv2.minMaxLoc(result)` ，其中，应该首先对图片进行处理：首先对图片进行边缘检测，然后对生成的图片使用： `cv2.cvtColor(bj_img_edge, cv2.COLOR_GRAY2RGB)` 。
    
    至于生成运动轨迹，就是结合 物理学运动公式，给予加速度，使前后速度不一样，先加速，再减速。更可以添加一个回拉的过程，更像人操作。
    
    这个版本有个问题，不知道是电脑运行速度的问题还是什么，在最后滑动滑块时，只是一点点的在运动，速度非常慢。
    

## 8.3 点触验证码的识别

# 第9章 代理的使用

## 9.1 代理的基本原理

### 1. 基本原理

代理：代理服务器： ***Proxy Server*** ，是网络的中转站，我们先将请求发送给代理服务器，然后代理服务器将请求再转交给目标网站，此时，目标网站识别的将不再是我们本机的 IP 地址。这就实现了 IP 的伪装。

### 2. 代理的作用

1. 突破自身 IP 访问限制，访问一些平时不能访问的站点
2. 访问一些单位或团体内部资源，比如校园网代理
3. 提高访问速度，通常，代理服务器都设置了一个较大的硬盘缓冲区，当有外界信息通过时，会同时将其保存到缓冲区，其他用户下载时，直接从缓冲区中读取信息。
4. 隐藏展示 IP 。

## 9.2 代理的基本使用

### 1.准备工作

需要先获取一个可用代理，代理就是 IP 地址和端口的组合， `<ip>:<port>` 这种格式，如果代理需要访问认证，那就还需要额外的用户名和密码两个信息。

主要就是需要获取代理，然后将代理 ip 加入代码中即可。

---

---

目前爬虫的学习就先告一段落了，刚才知道崔大神的第二版书已经发售了，而我学的第一版的好多内容都已经过时了，因此，先告一段落，接下来开始学习数据分析的知识，然后再学习深度学习。
后续可能仍会继续学习爬虫，毕竟还是挺有趣也挺有用的。纠结要不要买本新书。打个时间戳吧。 April 6, 2022