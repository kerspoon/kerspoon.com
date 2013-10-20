---
layout: project
categories: [projects]
description: A combination of a calculator, excel, and a calendar. It was made to help budgeting on my world travel. Developed in Java using Eclipse it is hosted on Github and uses Github Issues for project management.
image: mulcal.jpg
tags: [programming, java, eclipse]
---

**This is available online at <https://github.com/kerspoon/MulCal>.**

A calculator application that deals with:

+ currency conversion
+ VAT
+ date ranges
+ the usual equations (trig, logs, rounding)

It was made to help budgeting on my world travel. Developed in Java using Eclipse it is hosted on Github and uses Github Issues for project management. Every equation evaluated is stored as a history which can be annotated and used in later equations as constants. This history can be saved to use in excel.

It is currently command line based but the plan is to have a graphical front-end.


    7                 # the simplest possible 'equation'
    +6.8123e-2        # scientific notation
    7 + 1             # a function that doesn't need brackets
    4.1^2             # spaces are optional
    ((((-2.7))))      # extra brackets are ok
    sin -2            # a space is needed to seperate the function and the negative number
    5---2             # '-' can be part of a number, unary, or binary (one of each here)
    1 + 2 * 3 + 4     # order of precedence means this is different to the next one
    (1 + 2) * (3 + 4) # as the rules get changed as normal by brackets
    A + 1             # using the result of a previous calculation as a constant
    sin cos pi        # brackets are not enforced
    [GBP_USD 70]      # currency converting 70 from pounds to dollars
    tan [USD_YEN pi]  # brackets are not enforced
    [weeks 2010/2/4 2010/2/11]   # finds number of weeks (inc. fractional weeks) in a date range
    5 + 3 * 2 - 4 / (8 + 1) % A  #
    1+2-3*4/5^6                           # infix operators
    sin cos tan exp log sqrt signum abs E # prefix functions

