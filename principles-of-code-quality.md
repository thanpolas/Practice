# Principles of Code Quality

Tooling evolves, styling changes, languages come and go, but one thing remains constant. The pursue of code quality and engineering excellence.

## Decision-Making Process and Code

Every decision we make as engineers is a tradeoff. That does not mean, however, that we have to compromise our engineering principles. Naturally, the particular constraints, environment, resources, and goals are going to be the decisive factor, but there are underlying principles that should always be satisfied to achieve high code quality standards and engineering excellence.

Decisions don't just happen on the high level, like architecture or what particular technology to choose. They happen on each and every expression of our work. A newline that should be left between code blocks, a comment and what type should be made or not, when to line-break your code. All of these micro-decisions, draw the bigger picture that represents your coding discipline and reflects on the "quality" of your code and applications you work on.

Let's go through those principles and how and why they should all be factored into your decision-making process, no matter how big or small it is.

## Maintainability 

Maintainability helps engineers debug, update and extend existing code. The way this is achieved is through writing simple, explicit code. In other words, you should be able to run the debugger on a line-by-line basis or insert a console log statement in the code you are tasked with fixing or extending. 

For example, this is difficult to maintain code:

```js
function foo (alpha) {
    if (alpha) return bar();
    return null;
}
```

There are 2 maintainability issues with the above snippet: 

1. You are not able to extend what happens in the conditional unless you rewrite it.
1. You are not able to set a debug and examine the output of `bar()` before returning it.

This is how the same function can be written and be more maintainable:

```js
function foo (alpha) {
    if (alpha) { 
        const res = bar();
        return res;
    }
    return null;
}
```

Yes, this is more extensive, has more characters, and creates a variable. But none of those concerns are big enough compared to maintainability. We are no longer writing software for 8bit machines with 8kb of RAM, it's gonna be ok.

## Readability

Readability is the most important code quality factor. After all, we write code for humans reading it; computers have no trouble executing readable or obfuscated code, it's all the same to them (almost).

When working in teams, a uniform and homogeneous codebase is what readability is all about. Multiple developers are expected to read and understand existing code, so leadership and each engineer, should always have at high priority code homogeny when authoring code.

To achieve codebase uniformity and homogeneity a certain set of rules must be agreed upon and honored by all authors. When applied properly, the whole codebase should look like it was authored by a single person.

A hard to read example:

```js
function a(a, i) {
  a.splice(0, i);
  a.splice(1);
}
```

The same function in a more readable format:

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

Yep, documentation can make all the difference. The human brain can read words faster than it can read code, we are not machines. Larger and explicit argument names also help in understanding the implementation faster.

Readability spreads in almost any coding decision-making, how many lines of code should a file have? (no more than 300, others would be even more strict). Variable names, should they be short or long and explicit? (long and explicit). This isn't about writing an exhaustive list of rules, it's about the mindset and how to think about each problem.

Rule of thumb: anything that can save milliseconds in the effort of reading and understanding something, is a decision towards the good direction.

## Verification

Your work needs to be verified. Code is complicated and as we all know, full of errors and bugs. When you deliver your work, you have to somehow provide evidence that what you've built, works. The best way to do that is through automated testing.

While testing and testable code is also a major chapter of maintainability, it is so huge it deserves to be its own principle. Tested code gives more confidence to engineers. They can maintain a codebase and perform refactorings with the safety net of a complete test suite, which will prevent them from breaking existing functionality.

Automated testing and verification is not something abstract, it has a concrete footing in computer science. The least you can do to measure your performance on that front is to monitor your "test coverage". Just search for test coverage tools and libraries for your particular stack and make sure to integrate them into your pipeline.

And talking about pipelines, a fully automated build, test, and deployment pipeline is a requirement for any healthy codebase. It solves a lot of questions in regards to how the organization does operations. It saves the entire team time and of course, protects from breaking code entering production.

Aside from science, there is an art to testing, and it can only be developed through constant practice and application. I will close with my favorite line on the subject: 

> Untested code is legacy code from the moment it is written. And no one wants to deal with legacy code.

## Scalability

Scalability is about having processes, documentation, and operations that allow for rapid scalability of the codebase and the engineering team. This does involve code writing but also goes far beyond that. In regards to coding, the best practices towards that goal have already been established by Eric Evans in his book [Domain Driven Design][ddd]. A rule of thumb would be to make sure your business units are sufficiently decoupled and prepared to become a stand-alone micro-service at a moment's notice.

A more practical way to illustrate this, is the following, typical directory structure...

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

The other facets of scalability are documentation, operations, and process. Having onboarding documentation that explains step by step what a new engineer needs to do and install to be set up and ready to contribute, saves everyone days lost in back and forths. 

Processes and ceremonies that help collaboration, information dissemination, and exchanging experiences, all raise the ability of an organization to scale up.

## Epilogue

As we start in the programming industry, our brains are exploding with ideas of the possible and opinions on technologies. That is only natural and justified to a degree. This phenomenon has been responsible for moving entire industries, to better or worst.

Being a good programmer, producing quality code is an attainable skill. Yes, there is the science to computing, but there is also engineering excellence. Excellence comes through discipline. It's that discipline that needs to be developed and honed through your professional career that will make you a better programmer.

Please feel free to make your suggestions and share your ideas, this is an ever-living document/repo, where we all strive to get better.

Thank you for your attention 🙏.



[ddd]: https://www.goodreads.com/book/show/179133.Domain_Driven_Design
