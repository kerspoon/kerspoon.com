---
layout: project
categories: [projects]
description: A Lisp like programming language (called LiPy2) written to demonstrate certain programming techniques. It has prototype objects like Javascript and Lua as well as basic macros. It is written in Python using Emacs.
image: lipy2.jpg
tags: [programming, lisp, python]
---

**This is available online at <https://github.com/kerspoon/lipy2>.**

I have been developing LiPi to teach me various programming concepts. It is a small [lisp/scheme](http://schemers.org/) like programming language made in [python](http://www.python.org/).

It is broken down into a number of separate modules:

+ lex - tokenise a string into a list of string tokens
+ parse - convert tokens into LiPi datatypes
+ datatypes - all the data in scheme is of one of these types
+ environment - anything defined in lipy get stored in an environment
+ function - all built in lipy function calls (including special forms) as well as the default environment
+ main - tests and misc
+ prelude - some default scheme functions taken from Haskell

Each datatype can define a number of different operations which makes up the core of the program:

+ *eval* - this is what gets called when it is evaluated.
+ *str* - this turns it into a string for output.
+ *apply* - this deals with it being called like a function.
+ *eq* - tests for equality

Even the datatypes of `function` and `class` are handled this way. For instance a tidied version of the apply function for Lambda (the datatype of functions) is below:


    def __call__(self, args, env):
        """__call__ :: SchemePair -> Environment"""

        if self.macro:
            # expand in a new env
            mac = self.expand_macro(args, env)
            # call in the *old* env.
            return mac.scm_eval(env)

        # eval all args and return as a list
        evaled_args = [arg.scm_eval(env) for arg in to_list(args)]

        # extend the Environment with the new frame
        # the new frame is simply the evaled args mapped to the
        # parameters of the function
        new_env = extended_env(self.scm_vars, evaled_args, env)

        # eval the body of the lambda in the new Environment
        return self.body.scm_eval(new_env)


Note that macros are simply a function that doesn't eval it's arguments before being called. Instead it calls the function once to expand the macro and then calls the result as a normal function.

It has a test suite of around 200 different items. These are mostly basic functionality checks. As it lacks a lot of important system calls it is not suitable as a general programming language.

This is my 5th lisp implementation, the previous ones have been in C++, D, D again, and a previous version in Python.
