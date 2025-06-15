---
title: "Paying Attention to Details As a Developer"
datePublished: 2024-01-07T23:16:39.778Z
slug: paying-attention-to-details
cover: https://images.unsplash.com/photo-1579019874729-ffca9e9fe11c?q=80&w=2970&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
tags: frontend, web-development, programming, software-engineering

---

I recently got the chance to work with some individuals on a project. Most of the open source 
contributions I've done did not really have a specific set of designs to follow, 
so each contributor had to hack their way into building something that at the end, will be appealing. That was very easy and straight to the point so it was a lot of fun.

This time around, I had to work with a team of designers and other developers to build a project.
The designs weren't really complex but I managed to mess up a lot of things. Just like my other contributions, _I tried to get many things things done and in a short time_. This made me make a lot of mistakes that sometimes made me feel soo stupid when they were brought forth by the designers and other developers. The period of working with these people made me realize that it is not all about getting things done swiftly but also ensuring you get them done correctly.

You see, User Interfaces are not like backend APIs or SQL queries that are mostly not device specific. Once you write your select statement correctly, it will work on any database. Once you write your API correctly, it will work for any device that requests for it correctly, I mean, you get the point. But then, this is not the case with UIs. You have to ensure that your UI works on all devices and that it looks the same on all devices. This is where the problem lies. _Measurements are very different here and there can be several different measurements for different devices, so you have to ensure that you get the measurements right and also getting the interactions right_. (I mean, think about the number of android devices out there, you have to ensure that your UI works on all of them 😅).  



Getting into the specifics of the project, I had to build a landing page that was designed in figma. Every design comes with their specific design guides such as spacing, font sizes, user interaction feedbacks, shadows, and the list goes on. 

When I started out, I did not really pay attention to these, my ultimate goal was this: **Get it done and get it done extremely fast**. It is good to get things done quickly but not at the cost of not producing the right stuff. Every pull request I submitted, there was a little issue, and most of these issues are some of the most obvious things I overlooked. Some of these issues were:

- **Using wrong margins and paddings**: As an avid tailwindcss user, I was used to using the default utility classes I thought were right based on my Eye test (Eye Driven Development 😂). I did not really pay attention to the design guide and I ended up using the wrong classes. This was a very big issue because it made the UI look slightly different from the design which obviously the UI designers were not happy about. Having these things pointed out to me all the time really made me feel bad because I knew I could have done better.

- **Using wrong font weights**: When designing, font sizes are usually not the problem here, but then the weights of the font vary greatly and are not always determined by just looking at the design in the figma file unless that particular element is inspected to see the actual font weight. I made a couple of these mistakes and in the end, I had to go back and make a lot of changes to the codebase.

This list goes on and on but then, I will stop here.

Making all these mistakes made me realize something, it is good to develop things swiftly but you _must not compromise on the quality of the work you are doing_. It is better to take your time and get things done correctly than to rush and get things done wrongly. I am not saying you should not be fast, but then, you should not be too fast that you end up making a lot of mistakes. Remember, **Quality over Quantity**. 

Also note that we are all humans no matter how much you and your colleagues try to be perfect, you will still make mistakes. The most important thing is to learn from these mistakes and try not to repeat them again. _Too many mistakes can make people question your abilities_ and that is not a good thing so always try to do your best and pay attention to details. 


Before I sign off though, I will share some things I decided to do early in each project to ensure I always produce work that is of high quality. Some might be specific to some tools like TailwindCSS but then, you can always find the equivalent in your own stack.

- **Always read the design guide**: Quickly go through the design guide and see what the designers have to say about the project. This will give you a good idea of what to expect and what to look out for.

- **Setting up the right project configuration**: Now, I go through each design and note down all the colors that will used in the project. This I mostly do in the `tailwind.config.ts/js` file. I also note down the font sizes and font weights that will be used in the project. This will help me to always use the right classes when building the UI. This also makes it much easier to change things later along the line, like when the designers decide to change the font size of a particular element, you can just go to the config file and change it there and it will reflect across the whole project.

- **Using the right sizes**: In some cases were you might need to design a particular thing at just one point and you did not add the config for that, please do not rush into using the default utility classes that you think are right. It is better to use the exact value in the figma design than to use the wrong utility class. This will save you a lot of time and review stress. Example, say an element used in only one particular section has a font size of 45px. You might be tempted to use the `text-4xl` class but then, that is not the right class to use. It is better to use the `text-[45px]` class. This is what TailwindCSS calls the **Arbitrary Values**. You can read more about it [here](https://tailwindcss.com/docs/just-in-time-mode#arbitrary-values).

These are some of the things I have learnt and I hope you find them useful. If you have any suggestions, please let me know. I am open to feedback. Thanks for reading.