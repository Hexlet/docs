# Conceptual specifications

This article is about the idea behind Hexlet lessons and non-technical specifications. For technical specifications, please refer to [Technical specifications for lesson](theory-specifications.md).

## Overview

Hexlet lesson can include up to three parts:

* **Theory**. Goal: to introduce the user to some new concept or idea﻿.
* **Challenge**. Goal: to give them a chance to continue learning by building something, by solving a problem﻿.
* **Quiz**. Goal: to verify the skills acquired in first two steps.

## General specifications

* Lessons are **not building blocks of courses**. Lessons are independent and should be designed in a way that allows independent learning in any order and combination of lessons.
* Each lesson should cover a **single skill or concept**, should not be heavily connected to other lessons. Generally speaking, lessons should make perfect sense on their own.* Lesson should **get to the practice** as soon as possible. Do not spend time explaining the history of a programming language, for example. Instead, show the sample code right away, explain it and proceed to the challenge.
* Give your lesson a **complete name**. It should make sense without context. So, "Lesson 4" is BAD, "Introduction to anonymous functions in JavaScript" is GOOD.
* **Define the audience** clearly and follow that definition. A lesson might be designed for absolute beginners or experienced programmers, but not for both. So, for example, don't casually mention multithreading to absolute beginners, it will scare them off. Similarly, do not explain what variables are to experienced programmers.

## Theory specifications

* Theory should take around **20 minutes** to complete. So, it can be a 20 minute video or some text that takes 20 minutes to read. Or combination of two. If your theory part is larger – split that lesson into several.
*  If you use slides (presentation), make it in **English only** (even if your lesson is in Russian).

## Challenge specifications

* It should normally take no more than 2 hours to complete the challenge.
* If there are many steps in a single challenge exercise, think about splitting it into multiple exercises or even multiple lessons altogether.
* We highly recommend to include exactly three challenge exercises in one lesson. This way users are engaged, but not overwhelmed.

## Quiz specifications

* Quiz should include at least 10 questions.
* Do not test users' memory. Questions should be about concepts and ideas, not syntax.
* Include the knowledge users suppose to get after completing the challenge. Don't limit the questions to the theory.
