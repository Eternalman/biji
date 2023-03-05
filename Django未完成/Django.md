## Django基础知识

Django库安装

```python
pip install Django
```

#### 0.配置目录

```python

import os
from pathlib import Path

# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent

# Quick-start development settings - unsuitable for production
# See https://docs.djangoproject.com/en/4.0/howto/deployment/checklist/

# SECURITY WARNING: keep the secret key used in production secret!
SECRET_KEY = 'django-insecure-tpl3yxjk*vc#l0v^n3mtgbs324sj5n(@6i@(2gq)u_#x@!)q@a'

# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = True

ALLOWED_HOSTS = []

# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    # 注册应用
    'app1'
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'Login.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        # 优先去项目的根目录的templates中去寻找模板
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = 'Login.wsgi.application'

# Database
# https://docs.djangoproject.com/en/4.0/ref/settings/#databases
# 数据库配置
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'login',
        'HOST': '127.0.0.1',
        'USER': 'root',
        'PASSWORD': '123456',
        'PORT': 3306
    }
}

# Password validation
# https://docs.djangoproject.com/en/4.0/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]

# Internationalization
# https://docs.djangoproject.com/en/4.0/topics/i18n/
# 设置 语言
LANGUAGE_CODE = 'en-us'
# 设置 地区
TIME_ZONE = 'UTC'

USE_I18N = True

USE_TZ = True

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/4.0/howto/static-files/
# 静态文件存放地址默认在/static/
STATIC_URL = 'static/'

# Default primary key field type
# https://docs.djangoproject.com/en/4.0/ref/settings/#default-auto-field

DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

```



#### 1.创建项目

```python
# cmd下
令django-admin startproject 项目名
```

#### 2.启动项目

```python
# 进入到manage.py同级目录
python manage.py runserver
```

#### 3.创建应用

```python
# 进入到manage.py同级目录
python manage.py startapp 应用名
```

#### 4.项目结构

```py
一、项目目录结构
1.manage.py是项目管理文件，是Django用于管理本项目的命令行工具，后续的站点运行、 数据库自动生成、 静态文件收集等工作都需要通过该文件完成。
2.一个与项目同名的目录,这里是Login
 2.1.init.py是一个空文件，告诉Python该目录是一个Python包，创建后暂无内容。
 2.2.settings.py是Django项目的配置文件，里面包含了项目引用的Django组件、项目名等。后续开发中，还需要进行数据库参数配置、导入其他包等操作。
 2.3.urls.py是项目的URL配置文件。
 2.4.wsgi.py是定义WSGI的接口信息，用于与其他Web服务器集成，一般无需改动。
 2.5 asgi.py与ASGI兼容的web服务器，为项目提供服务的入口点，以便运行项目
 
 二、应用目录结构
init.py是一个空文件，表示当前目录app1可以当作一个python包使用。
tests.py文件用于开发测试用例，在实际开发中会有专门的测试人员，这个事情不需要我们来做。
models.py文件跟数据库操作相关。
views.py文件跟接收浏览器请求，进行处理，返回页面相关。
admin.py文件跟网站的后台管理相关。
migrations文件夹存放数据库的迁移文件。
apps.py文件为应用的属性配置文件
```

#### 5、应用注册

应用创建成功后，需要安装才可以使用，也就是建立应用和项目之间的关联。修改settings.py中的 INSTALLED_APPS配置项,加上你的应用即可

![image-20221124164451963](C:\Users\Administrator\Desktop\Django\图\image-20221124164451963.png)

#### 6、配置URL

  请求者在浏览器地址栏中输入url，请求到网站后，获取url信息，然后与编写好的URLconf逐条匹配，如 果匹配成功则调用对应的视图函数，如果所有的URLconf都没有匹配成功，则返回404错误。

##### 1.应用中创建urls.py

```python
# app1/urls.py中的代码如下

from django.urls import path
from app1 import views

urlpatterns = [
	path('index', views.index),
]

```

##### 2.项目中进行路由分发

```python
#  Skin/urls.py中的代码如下

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
	path('admin/', admin.site.urls),
	path('', include('app1.urls'))
]

```

#### 7、视图

  视图就是一个Python函数，被定义在views.py中。 视图的必须有一个参数，一般叫request，视图必须返回HttpResponse对象，HttpResponse中的参数 内容会显示在浏览器的页面上。 打开app1/views.py文件，定义视图index如下。

```python
from django.http import HttpResponse
def index(request):
	return HttpResponse("首页")

#去app目录下的templates目录寻找index.html （根据app的注册顺序，逐一去他们的目录中找）
 return render(request,'index.html')
```

#### 

![](图\image-20221124165539523.png)

#### 8、模板和静态文件

##### 1.每个子URL对应一个函数

url--->函数

##### 2.template目录模板

###### 2.1静态文件

在项目文件与manage.py同级目录下创建一个static文件夹

​	一般将‘图片’、“css”、“js”文件放到static目录里

![image-20221124202517294](图\image-20221124202517294.png)

​	在Django中，HTML中导入css、js文件要在页面标题加上`{% load static %}`方便日后的管理

![image-20221124203455983](图\image-20221124203455983.png)

​	在Django配置里静态文件默认是放在static目录的

![image-20221124203228249](图\image-20221124203228249.png)

###### 2.2HTML模板语法

（1）模板传参--------后端中必须将变量封装到字典中才允许传递到模板上

```python
return render(request,'xx.html',字典数据)
```

（2）模板变量名是由数字，字母，下划线和点组成的，不能以下划线开头

```html
{{ 模板变量名 }}
```

views.py

```python
def tm(requset):
    name = '小明'
    names = ['小红','小河','小米']
    return render(requset, 'tm.html', {'n1': name,'n2':names})
```

tm.html

```html
<body>
<h1>模板语法</h1>
<p>{{ n1 }}</p>
<p>{{ n2 }}</p>
<p>{{ n2.0 }}</p>
<p>{{ n2.1 }}</p>
<p>{{ n2.2 }}</p>
</body>
```

效果：

![image-20221124211441021](图\image-20221124211441021.png)

（3）for循环

```python
# HTML页面下
{% for i in list %}
	do something
{% endfor %}
```

views.py

```python
def tm(requset):
    names = ['小红','小河','小米']
    return render(requset, 'tm.html', {'n2':names})
```

tm.html

```html
<div>
    {% for i in n2 %}
        <span>{{ i }}</span>
    {% endfor %}
</div>
```

效果：

![image-20221124212353652](图\image-20221124212353652.png)

（4）模板变量解析顺序 

**方式一：{{ shop.name }}**

1）首先把shop当成一个字典，把name当成键名，进行取值shop['name'] 

2）把shop当成一个对象，把name当成属性，进行取值shop.name 

3）把shop当成一个对象，把name当成对象的方法，进行取值shop.name 

views.py

```python
def tm(requset):
    user_list = {'name': '小陆', 'age': 19, 'role': 'CTO'}
    return render(requset, 'tm.html', {'n3': user_list})
```

tm.html

```html
<hr/>
    {{ n3 }}
    {{ n3.name }}
    {{ n3.age }}
    {{ n3.role }}
<hr/>
```

效果：

![image-20221124215434140](图\image-20221124215434140.png)



**方式二：{{shop.0}}** 

1）首先把shop当成一个字典，把0当成键名，进行取值shop[0] 

2）把shop当成一个列表，把0当成下标，进行取值shop[0] 

如果解析失败，则产生内容时用空字符串填充模板变量。

views.py

```python
def tm(requset):
    user_list = {'name': '小陆', 'age': 19, 'role': 'CTO'}
    return render(requset, 'tm.html', {'n3': user_list})
```

tm.html

```html
<hr/>
    {{ n3 }}
    {{ n3.0 }}
    {{ n3.1 }}
    {{ n3.2 }}
<hr/>
```

效果：

![image-20221124215641960](C:\Users\Administrator\Desktop\image-20221124215641960.png)

**方法三：{% for i in n3.keys %}**

views.py

```python
def tm(requset):
    user_list = {'name': '小陆', 'age': 19, 'role': 'CTO'}
    return render(requset, 'tm.html', {'n3': user_list})
```

tm.html

```html
<div>
     # 循环n3里所有的键
    {% for i in n3.keys %}
        <span>{{ i }}</span>
    {% endfor %}
</div>
----------------------------------------------------------------------------
<div>
     # 循环n3里所有的值
    {% for i in n3.values %}
        <span>{{ i }}</span>
    {% endfor %}
</div>
----------------------------------------------------------------------------
<div>
     # 循环n3里所有的键和值
    {% for i,k in n3.items %}
        <p>{{ i }} == {{ k }}</p>
    {% endfor %}
</div>

```

效果**1**：

![image-20221124223209707](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221124223209707.png)

效果**2**:

![image-20221124224500683](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221124224500683.png)

效果**3**：

![image-20221124225429363](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221124225429363.png)

-------------------------------------------------------------------

**列表里包含字典**

views.py

```python
def tm(requset):
	data_list = [
        	{'name': '小刚', 'salary': 1888, 'role': 'CTO'},
        	{'name': '小余', 'salary': 2888, 'role': 'CT2'},
        	{'name': '小数', 'salary': 888, 'role': 'CT3'},
    	]
    return render(requset, 'tm.html', {'n4':data_list})
```

tm.html

```html
<hr/>
    <p>{{ n4 }}<p/>
   {% for i in n4 %}
        <div>{{ i.name }} {{ i.salary }} {{ i.role }}<div/>
    {% endfor %}
<hr/>
```

效果：

![image-20221125010308874](图\image-20221125010308874.png)

HTML的条件语句

tm.htnl

```html
{% if n1 == 'xxx' %}
	<div><div/>
{ elif n2 == 'xxx' %}
	<div><div/>
<% else %>
	<div><div/>
<% endif %></%%>
```

视图函数的render内部

1.读取含有模板的HTML文件

2.内部进行渲染（模板语法执行并替换数据），最终得到，只包含HTML标签的字符串

3.将渲染（替换）完成的字符串返还给用户浏览器 

#### 9.请求与响应

```python
# request 是一个对象，封装了用户发送过来的所有请求相关数据
def index(request):
	return render(request,xxx.html)

request.method   # 获取用户的请求方式
request.GET   # 获取通过URL上传递的参数   xxx/?n1=1234&n2=666
# 获取得到 {‘n1’:['1234'],'n2':['666']}
request.POST  # 获取通过请求体提交的数据 比如登录信息等
```

redirect

```python
# [响应]让浏览器重定向到其他网址
from django.shortcuts import render,redirect
def index(request):
	return redirect('https://baidu.com')
```































## Django进阶知识

### 一、**Django 亿些知识点**

#### 1.render()的用法

**render()**语法如下：

```python
render(request, template_name, context=None, content_type=None, status=None, using=None)
```

- request：浏览器向服务器发送的请求对象，包含用户信息、请求内容和请求方式等。
- template_name：设重模板文件名，用于生成网页内容。
- context：对模板上下文（模板变量）赋值，以字典格式表示，默认情况下是一个空字典。
- content_type：响应内容的数据格式，一般情况下使用默认值即可。
- status：HTTP状态码，默认为200。
- using：设置模板引擎，用于解析模板文件，生成网页内容。

#### 2.URL反向解析

总RUL：

```python
path('',include('子路由','子应用名字')，namespace='别名')
```

子URL：

```python
path('index', views.index,name='别名')
```

views.py

```python
def index(request):
    user = request.session.get('user', {})
    if user.get('username'):
        return render(request, 'index.html', {
            'username': user.get('username')
        })
    else:
        return redirect('student:login')## 别名
```

login.html

![image-20221122224630022](图\image-20221122224630022.png)

url的别名

![image-20230105225322998](图\image-20230105225322998.png)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![image-20230105225728155](图\image-20230105225728155.png)

#### 3.**多表关联**

```python
外键在一对多的多中设置：models.ForeignKey("关联类名", on_delete=models.CASCADE)
外键多对多
 tags = models.ManyToManyField('类名')
    
   ##查询的时候是
比如:xxx.tags
这里的tags属性就是关联表的实例化对象


##多表关联反向查询
正向：属性名
反向：小写类名加 _set
##反向查询前需要先获取到tag对象
例如：使用tag查询使用该tag的文章，需要先获取到该tag对象
```

**一些关键字**

```python
##第一个值
xxxx.first()
```

**模板语法**

```python
{%extends "base.html" %}

{% block base_nav %}
<p>11</p>
{% endblock base_nav %}


##模板加减法
{{变量|add:-1}}
{{变量|add:+1}}

```

#### 4.***分页***

```python
from django.core.paginator import Paginator


page_obj = Paginator(<可迭代的模型对象>,<单页数量>)##
page_obj.page(<页码>)##取单页
page_obj.num_pages ###一共多少页
page_obj.count ###总共多少条数据


```



### 二、**Django亿些实例**

#### **添加数据**

models.py     模型创建一个表：

```python
class Student(models.Model):# 定义一个模型
    stu_id = models.CharField(max_length=15, verbose_name='学生ID')
    stu_name = models.CharField(max_length=20, verbose_name='学生姓名')
    phone = models.CharField(max_length=20, verbose_name='学生电话')
    address = models.TextField(verbose_name='学生地址')
    department = models.CharField(max_length=20, verbose_name='院系')
    major = models.CharField(max_length=20, verbose_name='专业')

    class Meta():# 定义表名
        db_table = 'student'
```

urls.py      配置路由：

```python
path('add/', views.add, name="add")
```

views.py     视图配置：

```python
def add(request):
    # 如果是POST请求 
    if request.method == "POST":
        #前端填写的学号、姓名以及其他信息 返回到后端
        stu_id = request.POST.get('stu_id')
        stu_name = request.POST.get('stu_name')
        phone = request.POST.get('phone')
        address = request.POST.get('address')
        department = request.POST.get('department')
        major = request.POST.get('major')
        # 如果信息填写不完整
        if not all([stu_id, stu_name, phone, address, department, major]):
            context = {
                'error': '学生信息有遗漏',
            }# 给个提示有遗漏
            return render(request, 'add.html', context)
        # 数据库查询学号
        stu = Student.objects.filter(stu_id=stu_id)
        # 判断stu_id 是否重复
        if stu.exists(): #exists 存在的意思
            context = {
                'msg': '学号重复，请仔细核对',
            }
            return render(request, 'add.html', context)
        # stu_data 承接 数据库的Student表
        stu_data = Student()
        # stu_data.stu_id = 前端的学号
        stu_data.stu_id = stu_id
        stu_data.stu_name = stu_name
        stu_data.phone = phone
        stu_data.address = address
        stu_data.department = department
        stu_data.major = major
        # 最后在保存
        stu_data.save()
        context = {
            'sucess': '增加成功',
        }
        return render(request, 'add.html', context)
    else:
		# 加载 add.html页面
        return render(request, 'add.html')
```

## HTML页面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>增加学生信息</title>
    {% load static %}
    <link rel="stylesheet" href='{% static "css/style.css" %}'>
    <link rel="stylesheet" href='{% static "bootstrap/css/bootstrap.css" %}'>
    <script src="{% static 'bootstrap/js/bootstrap.js' %}"></script>
    <style>
        body {
            padding-top: 10%;
        }

        .container {
            width: 480px;
            margin: 0 auto;
            padding: 24px;
            box-shadow: 0 2px 12px 0 rgba(0, 0, 0, .1);
            background: #ffffff;
            border-radius: 6px;
        }

        .container .title {
            margin-bottom: 24px;
        }
        .container .form-group a {
            display: inline-block;
            width: 100%;
            color: #ffffff;
        }
    </style>
</head>
<body>
<div class="container">
    <h3 class="title">增加学生</h3>
    <form method="post" action="{% url 'student:add' %}">
        {% csrf_token %}
        <div class="form-group row">
            <label for="stu_id" class="col-sm-3">学生学号</label>
            <div class="col-sm-9">
                <input type="text" name="stu_id" placeholder="请输入学生学号" value="" class="form-control form-control-sm">
            </div>
        </div>
        <div class="form-group row">
            <label for="stu_name" class="col-sm-3">学生姓名</label>
            <div class="col-sm-9">
                <input type="text" name="stu_name" placeholder="请输入学生姓名" value=""
                       class="form-control form-control-sm">
            </div>
        </div>
        <div class="form-group row">
            <label for="phone" class="col-sm-3">学生电话</label>
            <div class="col-sm-9">
                <input type="text" name="phone" placeholder="请输入学生电话" value=""
                       class="form-control form-control-sm">
            </div>
        </div>
        <div class="form-group row">
            <label for="address" class="col-sm-3">学生地址</label>
            <div class="col-sm-9">
                <input type="text" name="address" placeholder="请输入学生地址" value=""
                       class="form-control form-control-sm">
            </div>
        </div>
        <div class="form-group row">
            <label for="department" class="col-sm-3">学生院系</label>
            <div class="col-sm-9">
                <input type="text" name="department" placeholder="请输入学生院系" value=""
                       class="form-control form-control-sm">
            </div>
        </div>
        <div class="form-group row">
            <label for="major" class="col-sm-3">学生专业</label>
            <div class="col-sm-9">
                <input type="text" name="major" placeholder="请输入学生专业" value=""
                       class="form-control form-control-sm">
            </div>
        </div>
        <div class="form-group row">
            <div class="col-sm-6">
                <button type="submit" class="btn btn-primary btn-sm" style="width: 100%">提交</button>
            </div>
            <div class="col-sm-6">
                <a href="{% url 'student:index' %}" class="btn btn-warning btn-sm">返回</a>
            </div>
        </div>
        {% if msg %}
            <div class="alert alert-primary" role="alert">
                {{ msg }}
            </div>
        {% endif %}
        {% if error %}
            <div class="alert alert-danger" role="alert">
                {{ error }}
            </div>
        {% endif %}
        {% if sucess %}
            <div class="alert alert-success" role="alert">
                {{ sucess }}
            </div>
        {% endif %}
    </form>
</div>
</body>
</html>
```

