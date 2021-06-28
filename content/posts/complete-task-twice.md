---
title: "Multiple SetResult on TaskCompletionSource"
description: "An attempt was made to transition to a task to a final state when it had already completed error does not get picked up by visual studio test runner"
date: 2021-06-27T20:00:50+02:00
author: "Sergiu"
language: "English"
tags: ["Tasks", "Task", "Async", "Threading", ".NET", "dotnet", "software", "software engineering"]
categories: ["Programming"]
--- 

### Background
Last week I was working on some end to end tests where we use an observable. This observable is using a TaskCompletionSource that we use to "close the subscription". When we got the data we expected from the observable we would call SetResult on our TaskCompletionSource.

To prevent the observable from running forever, we used a CancelationTokenSource with a timeout. When the timeout occurs we made it call SetResult on our TaskCompletionSource.

### Problem
This event occurs when the timer runs out, but our task was already completed. This means our code was trying to SetResult on an already completed task. 

We are using Xunit and with Visual Studio or Rider. Neither of them would catches the error, the tests would somehow just stop running with no extra information, it was extremely strange. 

### Discovery
Running dotnet test from the terminal actually failed the test with an "System.InvalidOperationException: An attempt was made to transition a task to a final state when it had already completed."  


## The fix
Simply replacing SetResult with TrySetResult solves the issue. 

I've included a sample Gist of the problem and the fix. 

<script src="https://gist.github.com/SergiuTalnaci/bbbd5b21246fec0cec3d7c0c76829dad.js"></script>