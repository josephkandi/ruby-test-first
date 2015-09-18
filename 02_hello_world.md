# Chapter 2: Hello World!

You’ve got your development environment set up as described in [Chapter 1](01_getting_started.md). So let’s write some code!

For decades, it has been traditional for programming texts to start with a [“Hello World”](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) program. This verifies that the development environment and input/output are functioning properly, but doesn’t do much else.

In keeping with the spirit of this book, we will write our “Hello World” program _test-first_—that is, we’ll write a test that states what we want the program to do, and then we’ll write the code to make the test pass.

## Set up a new project

Create a new directory (call it `ch02` or something) to hold this chapter’s Ruby files. If you’re using a Ruby version manager, you may want to put a configuration file in this directory to tell your version manager which Ruby to use (normally this file is called `.ruby-version`, but check the documentation for details).

Before you continue, make sure that your current directory at the command line is the `ch02` directory you just created.

## Create the test file

Since we are doing test-first development, we will start by writing a test (or in this case, a _spec_—more on that terminology in the next chapter). Create a file in the current `ch02` directory called `hello_spec.rb` with the following contents:

<pre><code class='lang-ruby'>
{% include "git+https://github.com/marnen/ruby-test-first-code.git/ch02/hello_spec.rb#02-hello-world-1" %}
</code></pre>

Even if you don’t yet know Ruby, you can probably guess that this means: when I run the code `{ hello }`, I want the output `Hello World!`. (We’ll explain the syntax in detail shortly.)

## Run the first test

Run the test by typing `ruby hello_spec.rb` at the command line. You’ll see output that ends with something like this:

```
  1) Error:
Hello World::hello#test_0001_prints "Hello World!":
NameError: undefined local variable or method `hello' for #<#<Class:0x007fa25c9782a8>:0x007fa25b8e9338>
    hello_spec.rb:5:in `block (3 levels) in <main>'

1 runs, 0 assertions, 0 failures, 1 errors, 0 skips
```

Obviously, the test has reported an error. This is entirely normal in test-first development: since we write the test before the code that makes it pass, we expect the first test run not to pass. Indeed, if it _did_ pass, we should be worried that we might have written the test incorrectly. This initial failure or error, then, is an important part of test-first development. If a test passes when we do not expect it to, we should always ask ourselves why.

In this case, the error is simple: ```undefined local variable or method `hello'```. This just means that we are referring to something named `hello`, but we have not defined it anywhere. Our test output, then, has told us exactly what our next step has to be: we must define `hello`.

## Create the implementation code

To define `hello`, we will start creating the code that actually implements the program itself, as opposed to the tests. Create a new file called `hello.rb` with the following contents:

<pre><code class='lang-ruby'>
{% include "git+https://github.com/marnen/ruby-test-first-code.git/ch02/hello.rb#02-hello-world-2" %}
</code></pre>

This defines `hello`, but does not have it do anything in particular.

Now that we have implementation code, we need to tell our test where to find it. Go back to `hello_spec.rb`, and on a new line immediately after the first line (and before the `describe` block), add:
```ruby
require './hello'
```

This tells our test to load the `hello.rb` file before going on with the body of the test.

## Rerun the test

Now run the test again with `ruby hello_spec.rb`. This time, the output should include
```
1) Failure:
Hello World::hello#test_0001_prints "Hello World!" [hello_spec.rb:6]:
In stdout.
Expected: "Hello World!"
Actual: ""
```

Notice that while the test is still not passing, the message is different. It is no longer complaining that `hello` is undefined—after all, we just defined it in `hello.rb`. This time, the test is telling us that it expected to see "Hello World!", but that the actual output was blank.

Just as with our previous test, the output from this failing test has told us what we need to do next: make the output not be blank.

## Make the test pass

Modify the `hello.rb` file so it looks like this:

<pre><code class='lang-ruby'>
{% include "git+https://github.com/marnen/ruby-test-first-code.git/ch02/hello.rb#02-hello-world-3" %}
</code></pre>

Run the test again. This time, you won’t see any annoying failure messages, but simply the following:

```
Run options: --seed 27490

# Running:

.

Finished in 0.048715s, 20.5275 runs/s, 20.5275 assertions/s.

1 runs, 1 assertions, 0 failures, 0 errors, 0 skips
```

By default the test runner does not print any details about passing tests, but we know our test has run because we can see that dot after the word `Running`. For each passing test, the test runner will print one dot, and in the last line, we can see that while it found one assertion (see below), it did not run into any failures or errors, so we know that our test finally passed.

In the terminology of testing, an _assertion_ or _expectation_ is a statement about the behavior we expect our code to have. In this case, our assertion was in the line `proc { hello }.must_output "Hello World!\n"`: we are _asserting_ that our code must have certain output in order to pass that test.

## Run the code

Now that the tests have passed, let’s run the program ourselves! Type `ruby -r ./hello -e 'hello'` to do this.[^1] Sure enough, you’ll see the output `Hello World!`—our program works just as the tests told us it would!

## Summary

In this chapter, we introduced the basic test-first workflow:
1. Write a small test
2. Watch it fail
3. Based on the failure, write just enough code to make the test pass

Writing a “Hello World” program in this way is admittedly overkill, but it serves as an introduction to the rhythm of test-first development. In the following chapters, we will expand on this notion of the test-first workflow, and we will use it to explain the Ruby language, as well as some more abstract notions of software engineering.

[^1] The `-r` command-line option loads (or _requires_) the specified file; it is equivalent to the `require './hello'` that we put in `hello_spec.rb`. The `-e` option treats the following string as a Ruby program, so that we are calling the `hello` function that we defined in `hello.rb`. Don’t worry too much about these options now: although they are helpful for getting up and running quickly, we shall see in the following chapters how to automate execution more efficiently.
