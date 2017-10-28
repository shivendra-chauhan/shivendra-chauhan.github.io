---
layout: post
title: "Writing Python in a Ruby Jekyll blog"
comments: true
categories: python, blog
---
I'm writing this blog to simplify the problems faced by a newbie to the programming world. I have my hands tied in a lot of different projects, mostly because the way I work is by doing long hours of research and writing the cleanest and sensible code. If I find code that I may not understand, I get a feeling that the computer is going to have a hard time too, compiling and interpreting it. So edit, edit, edit.. debug.

Today, I'm working to enhance this blog with my recent work with Python. My main aim is to have some python code visible to the user and also depict a graph at the end. I've looked through some datasets and want to figure what could I do with one "Indian Rails Time Table" from the year 2015.

Step 0(for preparation): I'll upload the dataset to my Github repository. I do not own copyrights to the dataset and have borrowed it from the data.gov.in for academic purposes.
Step 2: because step 1 is the hardest. I've realised, with most of the people I interact with, the fear of the beginning is the toughest part. I've also felt that if the water is cold, jump right in. If you wait for too long, your body becomes cold. So the best method for a newbie to start programming, is to get dirty with it. Don't pick up a notebook and pen to take some notes. Open a text editor and write

    print "Hello World"

Well, there you go, wasn't that bad was it? Now let's install some packages. If you're on Windows, you're gonna have to wait for my next blog. I love Mac and Linux. It's nothing personal, these are faster and let you take control for the most part. Open a new file in your text editor and name it app.py

    import numpy as np
    import pandas as pd

    f = pd.read_csv('trains.csv')

Let's clean up the data a little. Notice that the train numbers are objects and have single quotations at both start and end. To remove these:
    import re
I've just imported regular expressions library to try to get the integer out of the object. Next, I write the code.

    def train_num(str_num):
        p = re.search(r"([0-9]+)", str_num)
        return int(p.group())

    df['Train No.'] = df['Train No.'].apply(train_num)

Change the arrival and departure time data to pythonic datetime.time

    from datetime import datetime
    def time_hms(arr_dep):
        p = datetime.strptime(arr_dep, r"'%H:%M:%S'")
        return p.time()

    df['Arrival time'] = df['Arrival time'].apply(time_hms)
    df['Departure time'] = df['Departure time'].apply(time_hms)

    df.columns = df.columns.str.title().str.strip()

Functions are described beginning with a def keyword and can be used over and again as required. They're a lazy programmer's best friend but really you should want to avoid writing your code repeatedly making it easier to read.
