---
layout: post
title: Effective JUnit Testing with Eclipse
permalink: effective-junit-testing-with-eclipse
---

During refactoring or TDD you would like eclipse to run the appropriate junit test after each change of your class or test class. Ideally the test should run automatically after you save your class or test class in eclipse. 

There is a nice eclipse plugin for this job: [JUnit Flux](https://code.google.com/p/junitflux/)  

After installing, you can activate it via project's context menue: *Add JUnit Flux Nature*  

How does the plugin know, which test class to execute after save? This works with a naming convention for your test class, as described on the plugins [homepage](https://code.google.com/p/junitflux/).
