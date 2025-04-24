# EX01 Developing a Simple Webserver
## Date: 3/4/2025

## AIM:
To develop a simple webserver to serve html pages and display the list of protocols in TCP/IP Protocol Suite.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Import the necessary modules.

### Step 5:
Define a custom request handler.

### Step 6:
Start an HTTP server on a specific port.

### Step 7:
Run the Python script to serve web pages.

### Step 8:
Serve the HTML pages.

### Step 9:
Start the server script and check for errors.

### Step 10:
Open a browser and navigate to http://127.0.0.1:8000 (or the assigned port).

## PROGRAM:
### views.py
```
from django.shortcuts import render
def simpleweb(request):
    return render(request,'simpleserver.html')
```
### settings.py
```
from pathlib import Path
import os

BASE_DIR = Path(__file__).resolve().parent.parent




SECRET_KEY = 'django-insecure-!=n2vk$s^ny-2=&ae9b@@^0kw4w8#(viwh#n2l3-u97u&k1@i*'

DEBUG = True

ALLOWED_HOSTS = []




INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'web',
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

ROOT_URLCONF = 'simple.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
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

WSGI_APPLICATION = 'simple.wsgi.application'



DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}



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



LANGUAGE_CODE = 'en-us'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_TZ = True



STATIC_URL = 'static/'



DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

```
### urls.py
```
from django.contrib import admin
from django.urls import path
from web import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('simpleweb',views.simpleweb)
]
```
### simpleserver.html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Laptop Configuration</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: 'Roboto', Arial, sans-serif;
      background-color: #000;
      color: #ffeb3b;
      line-height: 1.6;
    }
    .container {
      max-width: 1200px;
      margin: 40px auto;
      padding: 20px;
      background: #111;
      border-radius: 10px;
      box-shadow: 0 4px 15px rgba(255, 235, 59, 0.2);
    }
    .header {
      text-align: center;
      padding-bottom: 20px;
      border-bottom: 2px solid #333;
    }
    .header h1 {
      font-size: 36px;
      color: #ffeb3b;
      margin-bottom: 10px;
    }
    .header p {
      font-size: 18px;
      color: #e0d400;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    th, td {
      padding: 15px 20px;
      text-align: left;
      border: 1px solid #333;
    }
    th {
      background-color: #222;
      color: #ffeb3b;
      text-transform: uppercase;
      font-size: 14px;
    }
    td {
      font-size: 16px;
      color: #ffeb3b;
    }
    tr:nth-child(even) {
      background-color: #1a1a1a;
    }
    tr:hover {
      background-color: #2a2a2a;
      transition: background-color 0.3s ease;
    }
    .highlight {
      background-color: #444;
      font-weight: bold;
    }
    @media (max-width: 768px) {
      .container {
        padding: 10px;
      }
      table {
        font-size: 14px;
      }
      th, td {
        padding: 10px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <h1>Laptop Configuration</h1>
      <p>A detailed overview of the specifications</p>
    </div>
    <table>
      <tr>
        <th>Configuration</th>
        <th>Details</th>
      </tr>
      <tr>
        <td class="highlight">Operating System</td>
        <td>Windows 11 Home Single Language 64-bit</td>
      </tr>
      <tr>
        <td>Processor</td>
        <td>13th Gen Intel(R) Core(TM) i5-13450HX (16 CPUs)</td>
      </tr>
      <tr>
        <td class="highlight">RAM</td>
        <td>16 GB</td>
      </tr>
      <tr>
        <td>Storage</td>
        <td>1 TB SSD</td>
      </tr>
      <tr>
        <td class="highlight">Graphics Card</td>
        <td>NVIDIA GeForce RTX 3050 (6GB)</td>
      </tr>
      <tr>
        <td>Screen Resolution</td>
        <td>1920 x 1080 (Full HD)</td>
      </tr>
      <tr>
        <td class="highlight">Screen Size</td>
        <td>15.6 inches</td>
      </tr>
      <tr>
        <td>Battery Capacity</td>
        <td>56 WHr</td>
      </tr>
      <tr>
        <td class="highlight">Weight</td>
        <td>2.8 kg</td>
      </tr>
      <tr>
        <td>Color</td>
        <td>Matt Black</td>
      </tr>
      <tr>
        <td class="highlight">Keyboard</td>
        <td>Orange-Backlit, QWERTY</td>
      </tr>
      <tr>
        <td>Wireless Connectivity</td>
        <td>Wi-Fi 6, Bluetooth 5.3</td>
      </tr>
      <tr>
        <td class="highlight">Ports</td>
        <td>USB-C, USB-A, HDMI, Ethernet</td>
      </tr>
      <tr>
        <td>Operating System Architecture</td>
        <td>64-bit</td>
      </tr>
    </table>
  </div>
</body>
</html>
```


## OUTPUT:
![image](https://github.com/user-attachments/assets/d0214caa-8590-418f-b6c2-cdc49de3aa98)


## RESULT:


## RESULT:
The program for implementing simple webserver is executed successfully.
