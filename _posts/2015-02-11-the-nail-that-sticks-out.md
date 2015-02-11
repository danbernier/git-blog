---
title: '"The Nail That Sticks Out Gets Hammered Down"'
date: 2015-02-11
tagline: use natural language processing to obscure individual characteristics
timeline: February 2015
---

Use TF-IDF to take a doc from a corpus, and re-write its words.

"Daniel rode his bike into work today."

might become

"xxxxxx rxxe his xike into wxxk today."

(I think '-' would look better, but in markdown, two '--' turns into an emdash, and I don't ware to figure it out now.)

Or maybe use random chars instead of mask-out chars like "-", "*", or "x". Base the random char selection on the corpus' letter frequencies, and match case. So "Daniel"might become, idk, "Rtlesn".

## Method

Count up a corpus' words, count frequencies.

Now take a doc from it, grab the words, and for each word, look up its TF-IDF, and use that to decide how much to censor it: high TF-IDF gets highly censored.

{% highlight ruby linenos %}
def censor(word)
  amount = tf_idf(word)  # 0..1
  chars = word.split('')
  chars.map { |char|
    if rand(1) < amount   # Linear P correlation
      '-'
    else
      char
    end
  }.join('')
end
{% endhighlight %}

Run this against different corpuses.

There will probably be some weirdness with masking the chars. Can you ever get 0%? 100%? Turning 0..1 into a probability threshold, you have eschelon problems. floor, ceiling. Maybe square the number, to push it towards the edges? No, wait, that'll only drag it down.

## Possible Corpuses

wikipedia pages, or...Oh! [Scott's alien documents thing](http://blog.scotterussell.com/post/108862070858/ufo-data-science-ufo-investigation-archive)?

What would it be like to run it against OKCupid profiles? Twitter bios? Tweets? About.me profiles? Book summaries? Github READMEs?
