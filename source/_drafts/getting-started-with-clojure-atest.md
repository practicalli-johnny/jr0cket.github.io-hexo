title: "getting started with clojure atest"
date: 2016-01-14 17:04:54
categories: 
tags: 
---


Overview


Setup / prerequisites


Writing your first tests



## The deftest function

is this a function or a macro ?  If a macro, is it valuable to see it expanded. ?

## The is function 



From ClojureDocs.org

deftest
clojure.test
Available since 1.1

    (deftest name & body)

Defines a test function with no arguments.  Test functions may call
other tests, so tests may be composed.  If you compose tests, you
should also define a function named test-ns-hook; run-tests will
call test-ns-hook instead of testing all vars.
 Note: Actually, the test body goes in the :test metadata on the var,
and the real function (the value of the var) calls test-var on
itself.
 When *load-tests* is false, deftest is ignored.

© Rich Hickey. All rights reserved. Eclipse Public License 1.0
2 Examples
link

;successful test example
(ns testing)
(use 'clojure.test)


(deftest addition
  (is (= 4 (+ 2 2)))
  (is (= 7 (+ 3 4))))
=> #'testing/addition

(deftest subtraction
  (is (= 1 (- 4 3)))
  (is (= 3 (- 7 4))))
=> #'testing/subtraction

;composing tests
(deftest arithmetic
  (addition)
  (subtraction))
=> #'testing/arithmetic

(run-tests 'testing)

=> Testing testing

Ran 6 tests containing 10 assertions.
0 failures, 0 errors.
{:type :summary, :test 6, :pass 10, :fail 0, :error 0}

link

;failure test example

;there is nesting, so when a leaf test fails so does its parents, in this example 2 tests fail, though there was only one real error.

(ns testing)
(use 'clojure.test)


(deftest addition
  (is (= 4 (+ 2 2)))
  (is (= 7 (+ 3 4))))
=> #'testing/addition

(deftest subtraction
  (is (= 1 (- 4 3)))
  (is (= 6 (- 7 4))))           ;error
=> #'testing/subtraction

;composing tests
(deftest arithmetic
  (addition)
  (subtraction))
=> #'testing/arithmetic

(run-tests 'testing)

=> Testing testing

FAIL in (arithmetic subtraction) (NO_SOURCE_FILE:669)
expected: (= 6 (- 7 4))
  actual: (not (= 6 3))

FAIL in (subtraction) (NO_SOURCE_FILE:669)
expected: (= 6 (- 7 4))
  actual: (not (= 6 3))

Ran 6 tests containing 10 assertions.
2 failures, 0 errors.
{:type :summary, :test 6, :pass 8, :fail 2, :error 0}

Log in to add an example
See Also
clojure.test/run-all-tests

Runs all tests in all namespaces; prints results. Optional argument is a regular expression; only ...
Added by boxie
clojure.test/run-tests

Runs all tests in the given namespaces; prints results. Defaults to current namespace if none give...
Added by boxie
clojure.test/is

Generic assertion macro. 'form' is any predicate test. 'msg' is an optional message to attach to ...
Added by jafingerhut
clojure.test/are

Checks multiple assertions with a template expression. See clojure.template/do-template for an exp...
Added by jafingerhut
clojure.test/testing

Adds a new string to the list of testing contexts. May be nested, but must occur inside a test fu...
Added by jafingerhut
clojure.test/test-var

If v has a function in its :test metadata, calls that function, with *testing-vars* bound to (conj...
Added by boxie



Thank you.
[@jr0cket](https://twitter.com/jr0cket)
