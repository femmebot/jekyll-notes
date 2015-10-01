# Notes on Jekyll, GitHub

#### Hosting Jekyll sites on GitHub

On GitHub, need to add the repo name for the base URL in the config file for sites that aren't at the root of the domain.

```
// in config file, make sure you precede with /

baseurl: '/repo-name'

// in header.html include to css path

{{ site.baseurl }}

```
 


#### Liquid for Designers

There are two types of markup in Liquid: **Output** and **Tag**  

Output markup is surrounded by curly braces:  
```
Hello {{ user.name }}

Hello {{ 'tobi' | upcase }}
Hello tobi has {{ 'tobi' | size }} letters!
Hello {{ '*tobi*' | textilize | upcase }}
Hello {{ 'now' | date: "%Y %h" }}
```
Refer to [Standard Filters](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers#standard-filters) and [Tags](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers#tags) for listing of methods and logic available with Liquid.

Supports if / else conditional logic:  
```
{% if user != null %}
  Hello {{ user.name }}
{% endif %}

{% if user.name == 'tobi' %}
  Hello tobi
{% elsif user.name == 'bob' %}
  Hello bob
{% endif %}

{% if user.name == 'tobi' or user.name == 'bob' %}
  Hello tobi or bob
{% endif %}

{% if user.name == 'bob' and user.age > 45 %}
  Hello old bob
{% endif %}

{% if user.name != 'tobi' %}
  Hello non-tobi
{% endif %}

```

Also supports case statements:  
```
{% case condition %}
  {% when 1 %}
    hit 1
  {% when 2 or 3 %}
    hit 2 or 3
  {% else %}
    ... else ...
  {% endcase %}

{% case template %}
  {% when 'label' %}
       // {{ label.title }}
  {% when 'product' %}
       // {{ product.vendor | link_to_vendor }} / {{ product.title }}
  {% else %}
       // {{page_title}}
  {% endcase %}
```

For loops:  
```
{% for item in array %}
  {{ item }}
{% endfor %}

// When iterating a hash, item[0] contains the key, and item[1] contains the value:
{% for item in hash %}
  {{ item[0] }}: {{ item[1] }}
{% endfor %}

// Reversing the loop
{% for item in collection reversed %}
  {{item}}
{% endfor %}

```


* [Liquid for Designers](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers)
