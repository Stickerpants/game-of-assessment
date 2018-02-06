# Project Guidelines

To write a non trivial project that takes about 2 days for an inexperienced developer to fully attempt. The project should demonstrate the skill of the developer across all areas that are crucial to modern day software development.

The project should be partitioned so that different components can be completed and tested without dependency on other sections. This is to make sure the developer can demonstrate their full skill in an area and not have it be hampered by lack of experience in another area. The emphasis is on assessing if the developer can write clean, maintainable code that is on par with acceptable standards. The project should not be answerable in whole by Google; but sections are OK to be Google-able. It should be easy to assess the correctness of the solution (either because it is easy to see, or because there is a test suite available to assert it against).

It is **not** expected that an inexperienced developer is able to finish every section. The baseline of someone who should be able to complete the project to full spec is a 3rd year Computer Science / Software Engineering major.

The language used should be around level of a novice developer. Terminology should be kept to a minimum, or should be explained on use. The vocabulary should also be accessible to younger developers, about 13 years of age or higher.

# Areas To Test

## Algorithmic thinking skills

* Can this developer decompose problems and write algorithms to solve the problem?
* What level of terminology does the developer use to communicate their algorithms and ideas?
* Is the developer effective at communicating their ideas?
* Does the developer use excessive or redundant buzzwords in their communication?

## Language mastery

* How fluent is the developer with their language?
* Does it feel like the developer is able to think "switch gears" and use the idioms of the domain?
* Has the developer picked an appropriate language to solve the problem?
* Do they fully utilize the features their language provides?
* Is the feature usage appropriate (and not heavy-handed) to the problem at hand?

## Design mastery

* Can the developer design a clean, appropriate class heirarchy?
* Does the developer utilize design patterns, where applicable?
* Has the developer designed their abstractions in an appropriate way?
* Is the abstraction well encapsulated?
* Are there anti-patterns, such as exessive (or improper) inheritance, or questionable design choices made?

## Justification and Reasoning

* Can the developer justify the choices they have made?
* Is it clear that the developer has invested time where its important?
* How accurately does the developer assess and prioritize tasks?
* Has the developer spent excessive amounts of time worrying about non-issues?

## Style

* Is it consistent?
* Is it readable?
* Does it follow the standards and conventions of the language they're working in?
* Is it clunky, like as if they're trying to apply another language's conventions?

## Quality

* Does the developer actively refactor?
* Does the developer write re-usable or extensible code?
* Does the developer keep their code orthogonal?
* Is the code well tested?

## Meta-development

* Does the developer future-proof and consider possible extensions where appropriate?
* Does the developer plan before they act, or do they just jump directly in and try to hammer it out?
* Does the developer use documentation and help effectively?
* Does the developer "reinvent the wheel" excessively, or without good justification?
* Does the developer write code that is just "good enough", like they don't care?
* Does the developer tunnel-vision on very specific problems, without seeing the bigger picture?

# Feedback

When giving feedback to solutions a developer has made, focus on objective criticism written in a third-person neutral tone. For example, instead of saying "You wrote this part wrong", we can better phrase it as "This part can be improved by doing \_\_\_\_\_\_ instead".

The general structure you should aim for give in advice is outlined below.

1. Explicitly identify the problem.
	* Sometimes, it may be hard for an inexperienced developer to recognize something that might seem immediately obvious to you.
2. Explain the reasoning behind *why* said thing is a problem.
3. Ask thought-provoking questions that leads the reader to a better understanding of the problem as a whole.
4. Give a concrete solution the problem in a different context.
	* i.e. Don't outright give away the solution to the problem. Instead, solve something similar, as a way to guide the reader into solving the original problem themselves.
	* One can also give a partial solution, and then lead the reader into solving the rest.
5. Point out anything the reader did correctly, to reinforce positive habits.

Ideally, try to avoid giving feedback on things that are largely a matter of preference. Avoid nitpicking syntax and style, unless you believe it to negatively impact the readability or maintainability of the code.

If you disagree with a design choice they've made, make sure to outline the context and assumptions you've made as part of your reasoning. For example, if someone's implemented a complicated design pattern that is overkill for the problem at hand (but is sound and cogent code), make sure that you don't give the impression that their solution is wrong. Instead, state the context ("Since the problem is simple because of ..."), and then suggest an alternative design ("Instead, a simple `switch` statement would have been more appropriate in this case").
