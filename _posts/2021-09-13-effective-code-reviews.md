---
 title: A Guide to Effective Code Reviews
 tags: [best-practices, agile]
 style: fill
 color: light
 excerpt: This article covers the myths, benefits and best practices related to code reviews.
 comments: true
 categories: computer-science
 last_modified_at: 2021-04-22T22:20:02+05:30
 header:
  overlay_image: assets/images/blog/code-reviews/krishna-pandey-KNZHyTpre18-unsplash.jpg
  overlay_color: "#000"
  overlay_filter: "0.5"
---

## Introduction
In this article we will cover 
- Myths & stigmas related to code reviews
- Why do we need code reviews at all?
- Effective tools to ease the process
- How to effectively code review an PR
- How to submit an effective PR


## Myths related to Code Reviews
Some popular myths related to code reviews are:
1. **Code Reviews are time-consuming:** This is the most common myth that people believe. Code reviews certainly need time to catch design issues & bugs and share knowledge across the team. Teams that do not have an effective code review process at all are already moving towards an unknown technical debt.
2. **Code reviews should only be done by senior developers:** Junior developers and new developers joining the team  should also be given a chance to review the code for knowledge sharing and a different perspective. 
3. **If you have unit tests, then you don't need the code review:** Unit tests are very very important! But they can never replace code review process. 


## Why do we need code reviews at all?

> “Truth can only be found in one place: the code.” 
― Robert C. Martin, Clean Code: A Handbook of Agile Software Craftsmanship

Before we look at the benefits of code reviews, it is important to know that writing clean
code is very important. 

Readability matters a lot! Why?
> Indeed, the ratio of time spent reading versus writing is well over 10 to 1. We are constantly reading old code as part of the effort to write new code. ...
> [Therefore,] making it easy to read makes it easier to write. - Robert C. Martin, Clean Code: A Handbook of Agile Software Craftsmanship



Code review can reap a lot of benefits like:
1. **Finding bugs & design flaws:** Devs need to make sure that the checked in code is free of bugs and major design flaws. Yes, the bug can be caught in a unit test or manual QA, but why not eliminate it before that? Similarly, a correct design pattern can save multiple iterations of refactoring in the future. 
2. **Knowledge sharing:** Have you worked in a team where codebase knowledge is limited to few people? Person A is the only one who knows everything about Service X, and person B knows everything about Service Y. But, whenever they have to work on a task involving making a change in other service, they are not really conformable. Code reviews gives an opportunity to both the developers to understand code changes being done to other services.  
3. **Reduced lottery factor:** Lottery factory
4. **Clean & consistent codebase**: 
5. **Better estimations**

## Tools & Best Practices

### Style Guide

### Formatters & Lynters

### Unit Tests

### Continuous Integration & Coverage

## How to submit an effective PR

## How to effectively review a PR

## Conclusion

## References


