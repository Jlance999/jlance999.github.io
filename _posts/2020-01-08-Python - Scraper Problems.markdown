---
layout: post
title:  "Python: Amazon....API Scraper?"
date:   2020-01-08 12:41:42 -0400
categories: Python
---

So I was working on the GUI for the Amazon Scraper today, and was doing some small things to make it more stylistic/intuitive, at this point just trying to pull the scraped product title into the graph as the graph title instead of it simply reading "Live Graph" for a heading. While doing so I suddenly had this error occur:

```
    title = soup2.find(id= "productTitle").get_text()
AttributeError: 'NoneType' object has no attribute 'get_text'
```

I thought, alright, fair enough, I'll just revert to my last working implementation and compare the changes to see what went wrong. I did so, and got the same error. I thought maybe there was an update to Amazon's website, maybe it was now loaded in differently, or the variable I was looking for had had a name change, so I checked.

![image](/assets/images/2020-01-08 12_47_38-Amazon.com_ Synology DS418play NAS Disk Station, 4-bay, 2GB DDR3L (Diskless)_ Co.png)

Alright, the variable is the same, maybe its just being loaded in differently and I need to add a delay to the scraper or something else trivial, as I learned from my troubleshooting background, its usually logical to check for the most obvious possible issues and work my way down. Instead of adding a delay, I first checked to see if the html itself was even being parsed, to do this I simply added ```print(soup)``` on the line just before the error occured. This is where things got interesting.

```

<!--[if lt IE 7]> <html lang="en-us" class="a-no-js a-lt-ie9 a-lt-ie8 a-lt-ie7"> <![endif]-->
<!--[if IE 7]>    <html lang="en-us" class="a-no-js a-lt-ie9 a-lt-ie8"> <![endif]-->
<!--[if IE 8]>    <html lang="en-us" class="a-no-js a-lt-ie9"> <![endif]-->
<!--[if gt IE 8]><!-->
<html class="a-no-js" lang="en-us"><!--<![endif]--><head>
<meta content="text/html; charset=utf-8" http-equiv="content-type"/>
<meta charset="utf-8"/>
<meta content="IE=edge,chrome=1" http-equiv="X-UA-Compatible"/>
<title dir="ltr">Robot Check</title>
<meta content="width=device-width" name="viewport"/>
<link href="https://images-na.ssl-images-amazon.com/images/G/01/AUIClients/AmazonUI-3c913031596ca78a3768f4e934b1cc02ce238101.secure.min._V1_.css" rel="stylesheet"/>
<script>

if (true === true) {
    var ue_t0 = (+ new Date()),
        ue_csm = window,
        ue = { t0: ue_t0, d: function() { return (+new Date() - ue_t0); } },
        ue_furl = "fls-na.amazon.com",
        ue_mid = "ATVPDKIKX0DER",
        ue_sid = (document.cookie.match(/session-id=([0-9-]+)/) || [])[1],
        ue_sn = "opfcaptcha.amazon.com",
        ue_id = 'KCDPAWC1FJS7GNDF6DN5';
}
</script>
</head>
<body>
<!--
        To discuss automated access to Amazon data please contact api-services-support@amazon.com.
        For information about migrating to our APIs refer to our Marketplace APIs at https://developer.amazonservices.com/ref=rm_c_sv, or our Product Advertising API at https://affiliate-program.amazon.com/gp/advertising/api/detail/main.html/ref=rm_c_ac for advertising use cases.
-->
<!--
Correios.DoNotSend
-->
<div class="a-container a-padding-double-large" style="min-width:350px;padding:44px 0 !important">
<div class="a-row a-spacing-double-large" style="width: 350px; margin: 0 auto">
<div class="a-row a-spacing-medium a-text-center"><i class="a-icon a-logo"></i></div>
<div class="a-box a-alert a-alert-info a-spacing-base">
<div class="a-box-inner">
<i class="a-icon a-icon-alert"></i>
<h4>Enter the characters you see below</h4>
<p class="a-last">Sorry, we just need to make sure you're not a robot. For best results, please make sure your browser is accepting cookies.</p>
</div>
</div>
<div class="a-section">
<div class="a-box a-color-offset-background">
<div class="a-box-inner a-padding-extra-large">
<form action="/errors/validateCaptcha" method="get" name="">
<input name="amzn" type="hidden" value="CoqKrOBNDpyeCZZwTY24DA=="/><input name="amzn-r" type="hidden" value="/Synology-DS418play-Station-4-bay-Diskless/dp/B075ZNKCK4/ref=cm_cr_arp_d_product_sims?ie=UTF8"/>
<div class="a-row a-spacing-large">
<div class="a-box">
<div class="a-box-inner">
<h4>Type the characters you see in this image:</h4>
<div class="a-row a-text-center">
<img src="https://images-na.ssl-images-amazon.com/captcha/icyrpkip/Captcha_ibibfrrfia.jpg"/>
</div>
<div class="a-row a-spacing-base">
<div class="a-row">
<div class="a-column a-span6">
</div>
<div class="a-column a-span6 a-span-last a-text-right">
<a onclick="window.location.reload()">Try different image</a>
</div>
</div>
<input autocapitalize="off" autocomplete="off" autocorrect="off" class="a-span12" id="captchacharacters" name="field-keywords" placeholder="Type characters" spellcheck="false" type="text"/>
</div>
</div>
</div>
</div>
<div class="a-section a-spacing-extra-large">
<div class="a-row">
<span class="a-button a-button-primary a-span12">
<span class="a-button-inner">
<button class="a-button-text" type="submit">Continue shopping</button>
</span>
</span>
</div>
</div>
</form>
</div>
</div>
</div>
</div>
<div class="a-divider a-divider-section"><div class="a-divider-inner"></div></div>
<div class="a-text-center a-spacing-small a-size-mini">
<a href="https://www.amazon.com/gp/help/customer/display.html/ref=footer_cou?ie=UTF8&amp;nodeId=508088">Conditions of Use</a>
<span class="a-letter-space"></span>
<span class="a-letter-space"></span>
<span class="a-letter-space"></span>
<span class="a-letter-space"></span>
<a href="https://www.amazon.com/gp/help/customer/display.html/ref=footer_privacy?ie=UTF8&amp;nodeId=468496">Privacy Policy</a>
</div>
<div class="a-text-center a-size-mini a-color-secondary">
          © 1996-2014, Amazon.com, Inc. or its affiliates
          <script>
           if (true === true) {
             document.write('<img src="https://fls-na.amaz'+'on.com/'+'1/oc-csi/1/OP/requestId=KCDPAWC1FJS7GNDF6DN5&js=1" />');
           };
          </script>
<noscript>
<img src="https://fls-na.amazon.com/1/oc-csi/1/OP/requestId=KCDPAWC1FJS7GNDF6DN5&amp;js=0">
</img></noscript>
</div>
</div>
<script>
    if (true === true) {
        var elem = document.createElement("script");
        elem.src = "https://images-na.ssl-images-amazon.com/images/G/01/csminstrumentation/csm-captcha-instrumentation.min._V" + (+ new Date()) + "_.js";
        document.getElementsByTagName('head')[0].appendChild(elem);
    }
    </script>
</body></html>
```
 This is a lot to read, but these are the important bits: 

 ```
 <title dir="ltr">Robot Check</title>
<meta content="width=device-width" name="viewport"/>
<link href="https://images-na.ssl-images-amazon.com/images/G/01/AUIClients/AmazonUI-3c913031596ca78a3768f4e934b1cc02ce238101.secure.min._V1_.css" rel="stylesheet"/>
<script>

if (true === true) {
    var ue_t0 = (+ new Date()),
        ue_csm = window,
        ue = { t0: ue_t0, d: function() { return (+new Date() - ue_t0); } },
        ue_furl = "fls-na.amazon.com",
        ue_mid = "ATVPDKIKX0DER",
        ue_sid = (document.cookie.match(/session-id=([0-9-]+)/) || [])[1],
        ue_sn = "opfcaptcha.amazon.com",
        ue_id = 'KCDPAWC1FJS7GNDF6DN5';
}
</script>
</head>
<body>
<!--
        To discuss automated access to Amazon data please contact api-services-support@amazon.com.
        For information about migrating to our APIs refer to our Marketplace APIs at https://developer.amazonservices.com/ref=rm_c_sv, or our Product Advertising API at https://affiliate-program.amazon.com/gp/advertising/api/detail/main.html/ref=rm_c_ac for advertising use cases.
-->
<!--
Correios.DoNotSend
```

Amazon bot detection found us out! The shame. Now what? Do we just abandon our poor scraper who didn't even make it to a full useable program outside of the terminal? Do we chalk it up to a learning experience and move on? Absolutely not. The entire reason I took the time to do this project in the first place was to learn about Python, and hopefully build my first GUI driven application after all of the C projects schoolwork has haunted my nightmares with. I need a break from plugging algorithms into those unforgiving black and white screens, and I'm not ready for that break to be over. I have spent the morning mulling over this issue, and the possible ways to move forward.

# Manipulate the Header

I could simply change my header and restore the full funcitonality of the program.

## Pros
+ Easy
+ Restores full functionality of previously written code
+ Allows me to immediately go back to learning tkinter

 
## Cons
+ This issue could re-arise in the future
+ Amazon's servers probably hate web scrapers 
+ Increases maintenance needs of program moving forward


