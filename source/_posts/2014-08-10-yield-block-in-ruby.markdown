---
layout: post
title: "Yield and Block in Ruby"
date: 2014-08-10 11:02:12 +0700
comments: true
categories: 
---

Hi all, in this post, i will research something with ```yield``` and ```block``` in ruby

#Yield

###Basic

{% codeblock lang:ruby %}
def test
  p "test"
  yield
end
test { p  "yield" }
# => test
# => yield
{% endcodeblock %}

### With variable
{% codeblock lang:ruby %}
def test
  p "test"
  x = 2
  yield x
end
test { |x| p  "yield #{x}" }

# => test
# => yield 2
{% endcodeblock %}

#Block
###Basic 
{% codeblock lang:ruby %}
def test(&code)
  p "test"
  code.call
end

test { p "block call"}
# => test
# => block call
{% endcodeblock %}
###With variable
{% codeblock lang:ruby %}
def test(&code)
  p "test"
  n = 2
  code.call(2)
end
test { |n| p "block call #{n}" }

# => test
# => block call 2
{% endcodeblock %}
