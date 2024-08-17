---
dg-publish: true
title: Don't Write Comments
creator: CodeAesthetic
date: 2023-01-16
duration: 355 seconds
id: Bf7vDBBOBUA
uploader_id: "@CodeAesthetic"
channel_id: UCaSCt8s_4nfkRglWCvNSDrg
uploader_url: http://www.youtube.com/@CodeAesthetic
thumbnail: https://i.ytimg.com/vi/Bf7vDBBOBUA/maxresdefault.jpg
playlist: 
playlist-index: 
webpage: https://www.youtube.com/watch?v=Bf7vDBBOBUA
source: Youtube
transcript_type: Transcript
categories:
  - Education
tags:
  - Programming
  - C Language
chapters:
  - Comments lie Code Documentation What a class or API represents Interface expectations Code Comments
fps: 60
recommender: 
rating: 
---

- <div class="video dataview-list"><iframe src="https://www.youtube-nocookie.com/embed/Bf7vDBBOBUA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>


- The video [Don't Write Comments](https://www.youtube.com/watch?v=Bf7vDBBOBUA) was published by [CodeAesthetic](http://www.youtube.com/@CodeAesthetic) on 2023-00-16 and is 5 minutes, 55 seconds long.


# Transcript

It's time to get a bit controversial. I don't think you should write comments in your code pretty much most of the time. Here, we have some code where we expect the value to be 5 Looking at this code, it's not obvious what five signals. We could add a comment explaining what five is, but even better we can create a constant representing the variable instead. The if statement now reads like a comment: that we want status to be message sent. If your code is complex enough that it warrants a comment, you should instead see if you can simplify or refactor the code to make it better instead. Right now, this condition is complex enough that we add a comment explaining it, but we can simplify this by using variables to name parts of the expression. Now the condition reads like the comment does. So the comment is basically redundant and can be removed. When conditions are complex enough like this, you could also consider moving the whole condition to its own function. Now you don't need to decipher at all. Types can also make comments redundant. In C++, there's no built in memory management. You often have a function like this where you get back a thing, but we need to make clear who will take ownership of the thing. Ownership, meaning the responsibility to release the memory after everyone is done with it. In older C++, you pretty much had to rely on comments to do this. If you were given ownership of an object, you'd find out by reading the comments of the function. But C++ added a new type called unique_ptr. The type represents a unique reference to the object. So if you get one, congratulations! It's now your responsibility. The type tells you explicitly that you now own it without the need for a comment. And even better, the type makes it so you get a compile error if you do bad things with it. A comment doesn't do that. Likewise, if we have a function that returns an int, but that int is optional. We could add a comment saying that -1 means we're not actually returning a value. But even better, we could use a type. If we return an optional int instead, it's now obvious that we might not give a value. We can't miss the comment and not realize that we might get an invalid timestamp back. The user needs to handle a missing value or they'll get a compiler error. You might wonder why don't we just make our code high quality and add comments anyways? Isn't more comments just better? That ignores the problems with comments. Comments get bugs like code. When people make changes to code, they often don't update the comments to match. But unlike comments, we have tools to stop bugs from entering code. We have tests, compiler checks and limiting. We don't have any system like that for comments. Maybe one day we can have some static analysis tool that uses AI to determine if the code matches the comments and flags any discrepancies - there's a start up idea - but because of this I don't trust the comments even when they exist. Comments can lie, but code cannot. So when trying to understand what a piece of code does, I read the code. I never read the comments. Maybe it's just me. Do you guys find yourself reading comments to understand code? What I do read is code documentation. Code documentation describes the high level architecture and public APIs of a system. Code documentation differs from comments where comments describe the internals of how your code works. Documentation describes how you use the code. The world needs more high quality documentation, and while we could write the documentation for our code completely separated from our code, it makes sense to keep our documentation as close to the code as possible in order to try to help them stay in sync. Tools like Doxygen, pydoc and JavaDoc generate documents directly from code files and therefore change alongside our code. It's useful to document what a class or API represents and any expectations for interface definitions like thread safety, possible states or error conditions. This helps the consumers of the API know how to use it and also helps any new implementers of the interface know how they're supposed to operate and behave. The guidance I've given about comments still applies for documentation. If we write better APIs, our documentation will be more concise and less prone to errors. But I concede that you'll never be able to make all of the parts of the system obvious with pure code. I do think there's a few cases where you should consider comments: if the code does something non-obvious for performance reasons, a comment can help explain why the code looks weird. If the code is utilizing a specific mathematical principle or an algorithm from a particular source you might consider linking to the source to help future maintainers. There's this comic called comic strip, and one of the comics is about a guy telling a developer that one day we won't need code in the future because you'll be able to simply write a spec and the program will just write itself. The developers are casting retorts that code is just a more precise way of writing a spec. I mean, I think it's wrong. And A.I. is coming for all our jobs, and we should be afraid of the impending sociopolitical turmoil that comes when our best tool for distributing wealth, the job disappears. But alas, it still helps my point. Code is a much better way to express intent than comments about code. So in general, if you feel like you need human language to describe your code, see if you could make your code more human. What other cases do you think comments are needed?
