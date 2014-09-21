---
layout: post
title: "Ruby with learning Japanese"
date: 2014-09-21 16:04:49 +0700
comments: true
categories:
---

I started learn Japanese 3 years ago. It last 3 months. No i want to learn it again, so i review ```Hiragana``` and ```Katakana```. Today i start with ```Hiragana```. I want to find a way can help me with this thing, and beside that, i am a developer, so i want to use my knowledge in this major apply to learn Japanese.

I created 2 files. One is ```hiragana.rb``` that shows ```romanji``` character and i will write down ```Hiragana``` character. The other is ```hiragana_reading.rb``` that shows ```Hiragana``` character and i will read it out loud.

#Writing

{% codeblock lang:ruby hiragana.rb%}
TIME_SLEEP = 5
MAX_EXIST = 5
hiragana = ['a', 'i', 'u', 'e', 'o',
            'ka', 'ki', 'ku', 'ke', 'ko',
            'sa', 'si', 'su', 'se', 'so',
            'ta', 'chi', 'tsu', 'te', 'to',
            'na', 'ni', 'nu', 'ne', 'no',
            'ha', 'hi', 'fu', 'he', 'ho',
            'ma', 'mi', 'mu', 'me', 'mo',
            'ya', 'yu', 'yo',
            'ra', 'ri', 'ru', 're', 'ro', 'wa', 'o', 'n']
mark = {}
hiragana.each {|h| mark[h] = 0}
def display_hiragana(hiragana, mark)
  if (hiragana.size > 0)
    while true
      a = hiragana.sample
      if (mark[a] < MAX_EXIST)
        sleep(TIME_SLEEP)
        p a
        mark[a] += 1
        puts "\e[H\e[2J"
      else
        hiragana -= [a]
        # Play with the remaining characters
        display_hiragana(hiragana, mark)
      end
    end
  else
    p "Finish. You've done a greate job!"
  end
end
p "Let play with Hiragana!"
display_hiragana(hiragana, mark)
{% endcodeblock %}

Go to ```Terminal``` cd to the folder contains that file. Run ```ruby hiragana.rb``` and see what happen.

#Reading
{% codeblock lang:ruby hiragana_reading.rb%}
TIME_SLEEP = 3
MAX_EXIST = 5
hiragana = ['あ', 'い', 'う', 'え', 'お',
            'か', 'き', 'く', 'け', 'こ',
            'さ', 'し', 'す', 'せ', 'そ',
            'た', 'ち', 'つ', 'て', 'と',
            'な', 'に', 'ぬ', 'ね', 'の',
            'は', 'ひ', 'ふ', 'へ', 'ほ',
            'ま', 'み', 'む', 'め', 'も',
            'や', 'ゆ', 'よ',
            'ら', 'り', 'る', 'れ', 'ろ', 'わ', 'を', 'ん']
mark = {}
hiragana.each {|h| mark[h] = 0}
def display_hiragana(hiragana, mark)
  if (hiragana.size > 0)
    while true
      a = hiragana.sample
      if (mark[a] < MAX_EXIST)
        p a
        mark[a] += 1
        sleep(TIME_SLEEP)
        puts "\e[H\e[2J"
      else
        hiragana -= [a]
        # Play with the remaining characters
        display_hiragana(hiragana, mark)
      end
    end
  else
    p "Finish. You've done a greate job!"
  end
end
p "Let play with Hiragana!"
display_hiragana(hiragana, mark)
{% endcodeblock %}
You can go to terminal to increase the font size of ```Hiragana``` characters.
* MacOS: Terminal -> Preferences -> Profile -> Text, at Non-ASCII Font, you choose the bigger font: maybe 24 or 30px.

After that, you go to ```Terminal``` cd to the folder contains that file. Run ```ruby hiragana_reading.rb``` and see what happen.

**Notes:
To Write ```Hiragana``` character, in MacOS, you have to go to ```System Preferences``` -> ```Keyboard``` -> at Tab ```Input Sources```, you add ```Japanese``` keyboard. That's it.
For others OS, you do someway to enable Japanese Keyboard.
