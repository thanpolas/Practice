# Principles of Code Quality

Tooling evolves, styling changes, languages come and go — but one thing remains constant: the pursuit of quality code and engineering excellence.

## Decision-Making Process and Code

Every decision we make as engineers is a tradeoff. However, that does not mean that we have to compromise our engineering principles. Naturally, the particular constraints, environment, resources, and goals should be considered as determining factors in each case, but there are also underlying principles that should always be satisfied to achieve high quality code standards and engineering excellence.

Decisions don't just happen at a massive scale, as in the case of choosing a particular architecture or technology. They happen at every instance of our work. Consider the smallest examples: Shoulda new line be left between code blocks? When to comment, and what type should be made? A line-break in your code here, or there instead? All of these micro-decisions express parts of the bigger picture that, overall, reflects your coding discipline,the quality of your code and your expertise with the applications that you work on.

Let's go through these principles, and consider how and why they should all be factored into your decision-making process—no matter how big or small the decision is.

## Maintainability

Maintainability helps engineers debug, update and extend existing code. The way to achieve maintainability is to write simple, explicit code. In other words, to ensure that you can fix or extend code when necessary, you should be able to run the debugger on a line-by-line basis or insert a console log statement in the code.

For example, this is difficult to maintain code:

```js
function foo (alpha) {
    if (alpha) return bar();
    return null;
}
```

There are 2 maintainability issues with the above snippet:

1. You are not able to extend what happens in the conditional unless you rewrite it.
2. You are not able to set a debug and examine the output of bar() before returning it.

This is how the same function can be written to be more maintainable:

```js
function foo (alpha) {
    if (alpha) { 
        const res = bar();
        return res;
    }
    return null;
}
```

Yes, this is more extensive, has more characters and creates a variable. But none of those concerns are big enough to outweigh the value of maintainability. We are no longer writing software for 8bit machines with 8kb of RAM — it's gonna be OK!

## Readability

Readability is the most important code quality factor. After all, we should remember that we are writing code for the humans who are reading it; whereas computers have no trouble executing readable or obfuscated code (it's basically all the same to them).

When working in teams, readability consists in a uniform and homogeneous codebase. Multiple developers are expected to read and understand existing code, so leadership and every engineer should always give the highest priority to code homogeneity when authoring code.

To achieve codebase uniformity and homogeneity, a certain set of rules must be agreed upon and honored by all authors. When this set of rules is applied properly, the whole codebase should look like it was authored by a single person.

This is a hard to read example:

```js
function a(a, i) {
  a.splice(0, i);
  a.splice(1);
}
```

This is the same function in a more readable format:

```js
/**
 * Will remove all items from the provided array except the one with the defined
 * index.
 *
 * @param {Array} ar An array.
 * @param {number} arIndex the index item to retain.
 * @return {void} Array is updated in place.
 */
helpers.arrayKeep = (ar, arIndex) => {
  ar.splice(0, arIndex);
  ar.splice(1);
};
```

Yep, documentation can make all the difference! Unlike machines that process code alone, our human brains can more efficiently understand code when it’s accompanied by helpful documentation. Larger and explicit argument names also help to understand the implementation faster.

Readability is a concern in almost any coding decision-making: How many lines of code should a file have? (In my view, no more than 300, although others would be less generous). Regarding variable names: should they be short or long and explicit? (Long and explicit.) Ultimately, this isn't about writing an exhaustive list of rules. Rather, it's about developing a careful mindset that guides your decision-making and problem-solving.

A rule of thumb: Anything that can save even milliseconds in the act of reading and understanding code, is a development in the right direction.

## Verification

Your work needs to be verified. Code is complicated and, as we all know, full of errors and bugs. When you deliver your work, you should also  provide evidence that what you've built actually works.The best way to do that is through automated testing.

While testing and testable code is also a major part of maintainability, it is so important that it nonetheless deserves to be considered its own principle. Tested code gives more confidence to engineers. They can maintain a codebase and perform refactorings with the safety net of a complete test suite, which will prevent them from breaking existing functionality.

Automated testing and verification is not something abstract. It has a concrete footing in computer science. At the very least, you should monitor your "test coverage". Simply search for test coverage tools and libraries for your particular stack, and make sure to integrate them into your pipeline.

A fully automated build, test, and deployment pipeline is a requirement for any healthy codebase. It helps to solve questions regarding how the organization operates. It saves the entire team time and, of course, protects against  broken code from entering into production.

In addition to its science, there is also an art to testing, and it can only be developed through constant practice and application. I heed my favorite line on the subject:

> Untested code is legacy code from the moment it is written. And no one wants to deal with legacy code.

## Scalability

Scalability is about having processes, documentation, and operations that allow for rapid scalability of the codebase and the engineering team. This does involve code writing but also goes far beyond that. Regarding coding, the best practices for scalability have already been established by Eric Evans, in his book, [Domain Driven Design][ddd]. A good rule of thumb for operations is to make sure that your business units are sufficiently decoupled, and prepared to become a stand-alone micro-service at a moment's notice.

The following typical directory structure illustrates this practically ...

Do not do:

```
app/controllers/user.ctrl.js
app/models/user.model.js
app/views/user.view.js
```

Do:

```
app/users/user.ctrl.js
app/users/user.model.js
app/users/user.view.js
```

The other facets of scalability are documentation and process. Save everyone time by having onboarding documentation that explains, step by step, what a new engineer needs to do and install in order to be ready to contribute..

Processes and rituals that help collaboration, communication, and peer to peer learning, all improve the scalability  of an organization.

## Conclusion

As we get our footing in the programming industry, our minds swim with new ideas about what is possible, and with opinions on existing technologies. This phenomenon has been responsible for moving entire industries, for better or worse, but we should not let a desire for innovation get in the way of the best practices.

Being a good programmer, and consistently producing quality code, is attainable. Yes, there is a science to computing, but there is also the practice of excellence in engineering. Excellence comes through discipline. To become a better programmer, you should strive to develop and hone that discipline throughout your professional career...

Please, feel free to make your suggestions and share your ideas—this is an ever-living document/repo, where we all strive to get better.

Thank you for your attention 🙏.

[ddd]: https://www.goodreads.com/book/show/179133.Domain_Driven_Design
