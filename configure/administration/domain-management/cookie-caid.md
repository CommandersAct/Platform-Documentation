# Cookie CAID

## Introduction

The CAID cookie: your VIP pass for a top level tracking visitors on your website! \
\
🌐 Powered by Commanders Act, the CAID cookie, is your go-to for identifying and tracing a visitor's journey across different browsing sessions.

Its construction is essential, especially in the context of restrictions imposed by privacy and security policies such as ITP (Intelligent Tracking Prevention).

{% hint style="info" %}
The CAID is automatically created/managed by Commanders Act servers if you choose the proxy method (WAF or on-premise proxy)
{% endhint %}

**You must create it yourself, on your own server, in the case of "First Party" tracking via CNAME or A-Record**, but it is not necessary if you use a proxy. In this documentation, you'll find all the information you need to build it.

Ready to elevate your tracking game and conquer the challenges? \
Dive in, and let's make your On-Premise CAID cookie the superhero of your website! 🚀\


## How to setup your cookie CAID?

When creating your CAID's cookie, apply the following requirements:

### Cookie name&#x20;

&#x20;"**CAID**" (in uppercase)

### Cookie structure recommendation

:heavy\_check\_mark: Contains 20 random characters

:heavy\_check\_mark: Preceded by the year the cookie was created

<figure><img src="../../../.gitbook/assets/image (493).png" alt=""><figcaption></figcaption></figure>

:tada: Available on the entire domain and its sub-domains.\
:rocket: Accessible client-side and server-side

### Lifetime

:heavy\_check\_mark:Cookie's expiry date: maximum **13 months** after creation date.

### Creation and Deposit

:heavy\_check\_mark:Created by the company server (On-Premise).\
:heavy\_check\_mark:Deposited on the main domain and all associated sub-domains. (.mydomain.com)

### Accessibility

:heavy\_check\_mark:Accessible to all, including servers and JavaScript scripts on the page.

## Code snippets

Here are some examples of snippet code to create your On-Premise CAID cookie

{% tabs %}
{% tab title="PHP" %}
```
<?php ​
$cookie_name = "CAID";​
$year = date("Y");​
$random_numbers = substr(str_shuffle(str_repeat('0123456789', 20)), 0, 20);​
$cookie_value = $year . $random_numbers;​
$expiration = time() + (13 * 30 * 24 * 60 * 60); // 13 mois ​
$path = "/"; // Disponible sur tout le domaine​
setcookie($cookie_name, $cookie_value, $expiration, $path);​
?>​
```
{% endtab %}

{% tab title="Node.js" %}
```
//Node.js with package "express"
const express = require('express’);​
const app = express();​

function generateRandomNumbers() { ​
return Array.from({ length: 20 }, () => Math.floor(Math.random() * 10)).join(‘’); ​
} ​

app.get('/', (req, res) => { ​
   const year = new Date().getFullYear(); ​
   const randomNumbers = generateRandomNumbers(); ​

   res.cookie('CAID', year + randomNumbers, { maxAge: 13 * 30 * 24 * 60 * 60 * 1000, // 13 months in milliseconds​
      path: '/’, ​
      httpOnly: true // Sécurité renforcée ​
   }); ​

   res.send('Cookie set'); }); ​

app.listen(3000, () => { ​
   console.log('Server is running on port 3000’); ​
});​
```
{% endtab %}

{% tab title="Python" %}
<pre><code>// Python with "Flask"
from flask import Flask, make_response ​
from datetime import datetime, timedelta ​
import random ​
app = Flask(__name__) ​
def generate_random_numbers(): ​
    return ''.join([str(random.randint(0, 9)) for _ in range(20)]) ​
@app.route('/’) ​
def set_cookie(): ​
    resp = make_response("Setting cookie") ​
    expire_date = datetime.now() + timedelta(days=13*30) ​
<strong>    year = datetime.now().year ​
</strong><strong>    random_numbers = generate_random_numbers() ​
</strong>    resp.set_cookie('CAID', f'{year}{random_numbers}', expires=expire_date) ​
    return resp ​
if __name__ == "__main__": ​
<strong>    app.run(port=5000)
</strong></code></pre>
{% endtab %}

{% tab title="Ruby" %}
```
require 'sinatra’ ​
require 'securerandom’ ​

get '/' do ​
random_numbers = SecureRandom.random_number(10**20).to_s.rjust(20, '0’) ​
year = Time.now.year ​
response.set_cookie('CAID', { value: "#{year}#{random_numbers}", expires: Time.now + (13 * 30 * 24 * 60 * 60), path: '/' }) "Cookie set" ​
end​
```
{% endtab %}
{% endtabs %}
