# Conceptual specifications

This article is about the idea behind Hexlet lessons and non-technical specifications. For technical specifications, please refer to [Technical specifications for lesson](technical-specifications.md).

## Overview

A Hexlet course is a short, concise course which covers a particular area. We believe that most of traditional large courses should be divided into smaller parts, for example, "C programming language" is actually a number of courses – "Intro to C", "Memory management in C", "Working with files in C", etc.

Hexlet lesson can include up to three parts:

* **Theory**. Goal: to introduce the user to some new concept or idea.
* **Exercise**. Goal: to give them a chance to continue learning by building something, by solving a problem.
* **Quiz**. Goal: to verify the skills acquired in first two steps.

## General specifications

* Although lessons are building blocks of courses, they should be as independent as possible, so that they provide a way for independent learning in any order and combination of lessons.
* Each lesson should cover a **single skill or concept**, should not be heavily connected to other lessons. Generally speaking, lessons should make perfect sense on their own.* Lesson should **get to the practice** as soon as possible. Do not spend time explaining the history of a programming language, for example. Instead, show the sample code right away, explain it and proceed to the challenge.
* Give your lesson a **complete name**. It should make sense without context. So, "Lesson 4" is BAD, "Introduction to anonymous functions in JavaScript" is GOOD.
* **Define the audience** clearly and follow that definition. A course might be designed for absolute beginners or experienced programmers, but not for both. So, for example, don't casually mention multithreading to absolute beginners, it will scare them off. Similarly, do not explain what variables are to experienced programmers.

## Theory specifications

* Theory should take around **20 minutes** to complete. So, it can be a 20 minute video or some text that takes 20 minutes to read. Or combination of two. If your theory part is larger – split that lesson into several.
*  Stick to one language. If your lesson is in Russian, everything should be in Russian: titles, slides, questions, comments, etc.

## Exercise specifications

* It should normally take no more than 30 minutes to complete an exercise.
* First exercises in the course should be very simple. This will help build up user's confidence and help them progress further. For example, in the introductory courses about programming languages first exercise usually is a simple "change this one line" sort of problem.
* If there are many steps in a single challenge exercise, think about splitting it into multiple exercises or even multiple lessons altogether.

## Quiz specifications

* Quiz should include at least 5 questions and at most 15.
* Do not test users' memory. Questions should be about concepts and ideas, not syntax.
* Include the knowledge users suppose to get after completing the exercise. Don't limit the questions to the theory.
