---
title: Inventory Actions Console
---

During my summer internship at Amazon, my primary project was to add significant functionality to the Inventory Actions Console, or IAC, a web application that serves as an inventory compliance management tool, allowing users to search and suppress defective inventory items.

The tool was originally created to replace a legacy system that served a similar purpose, but had a few issues. For one, the codebase and tech stack were very outdated, and for another, the tool only supported taking action at the lowest granularity with minimal persistence, which opened the door for defective inventory leakages.

Out of these problems, the IAC was born, but when I first started my internship it was still in a skeleton phase. The basics for the UI were in place, and it used a more modern tech stack, but the actions it could take were still limited.

That's where my project fit in.

## What I Did

I added 3 new advanced search capabilities and corresponding granularities of action to the IAC, which allowed users to operate on different item identifiers and categories and enabled those actions to be persistent, so if a user took action on all of a seller's inventory for a particular item, any new inbound inventories would follow that action. This removed previous causes for inventory leakage.

There were also some design decisions made to improve the UI itself, including changing the method by which users choose which items to suppress/unsuppress to increase protection against inadvertent error and using the search parameters to infer what level to take action on, so those three new functionalities resulted in no additional mental overhead for the user.

## What I learned

This was my first industry software project, and I learned a lot from it! 

For one, I was exposed to a plethora of new technologies. I had a bit of experience in Java, which the back-end was written in, but I was able to solidify it over the summer. I learned how to write web applications in React. The application was also hosted on AWS, using serverless Lambda functions for the backend and API Gateway to handle the web requests, and deployed using the AWS CDK and CloudFormation.

It also raised the standard of my code. At the industry level, there's far more rigorous standards for things like robust unit and integration testing, optimization and efficiency, and scalability than I had ever been exposed to in small personal or academic projects.

While these presented challenges to me during the internship, they were the greatest sources of my growth as well.



