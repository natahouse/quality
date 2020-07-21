# nata.house Software Quality Guidelines

![](assets/cool-logo.jpg "NH logo")

This document describes specific programming practices that help ensure your final product will be easy and pleasant to use, both for end-users and other developers as well. The idea is to showcase some of these in order to remind our devs that every piece of software developed by nata.house must follow these practices, in order to make sure we are delivering the best possible product.

Please note that we won’t focus on specific coding practices here, the idea is to describe product requirements that should always be implemented when we are delivering, regardless of whether it was on the client’s requirement list or not.

This document is organized going from the most generic practices to the most specific ones. It currently has the following sections:

1. Software Projects                          ------ + Generic
2. Git
3. API Design
4. Web Development
5. Mobile Development/React Native
6. CSS
7. React Components                           ----- + Specific
  
*@CONTRIBUTE add gif or image to this section*
## 1. Software Projects

**Don’t use strings directly in your source code. Abuse declaring constants, in a separate file if they are going to be shared across the system or at the top of the file if it is to be used only once.**

*@CONTRIBUTE examples*

**Configure internationalization (in our case, usign i18n) in every project,even if there are no plans for translating it, because:**

* Makes it easier to maintain the app’s text content
* If the owner of the system decides they need a CMS, it will be easier to set up.
* Of course, makes it easy to internationalize the app
* Helps creating a mindset of componentization and separation of concerns
* Teaches you about a very common feature in today's applications (multilanguage)

*@CONTRIBUTE i18n react setup tutorial*

**Always use environment variables to store sensitive information. Do this from the beginning of the project, resist the temptation to leave it in the source code “just for now”. Examples of stuff that should be on your .env:**

* Database addresses and passwords
* API Keys
* API urls
* Auth secrets

*@CONTRIBUTE add more examples*
*@CONTRIBUTE environment variables react setup tutorial*
*@CONTRIBUTE environment variables node tutorial*

**Every serious project must have configured Continuous Integration/Continuous Deployment pipelines (CI/CD). It makes the shipping process much easier and saves a lot of the everyone's time. The pipeline must include:**

* Build process
* Deployment
* Static Code Analysis Tools (SonarQube, Coderbyte...)
* Storybook (if necessary)
* Automated tests

**Every project must have an updated README.md file, to **help** out your fellow programmers and make their lives a lot easier! Think about answering these questions when you are documenting your work on a repository:**

* How do I run it?
* How do I build it?
* How do I test it?
* What does it use?
* Which problems might I run into?
* What would I want to have known before running this project for the first time?
* How is the branch structure?

**Work out a development flow that makes sense! Document it and show it to people before having them work in the project. For example:**

*Pipeline*
`Regular Commit Pipeline: Any commit -> Trigger remote build -> Publish to Unique URL`

*Objectives*:

* Test you features post-build
* Find out at which specific point something stopped working or behaving differently
* Make code review easier
* Make QA tests easier
* Run tests

*Pipeline*
`Staging Pipeline: develop commit -> Trigger remote build -> Publish to staging URL`

*Objectives*:

* Test fully released/integrated features
* Replicate production environment as closely as possible
* Allow for testing of fully integrated features
* Allow final user testing before releasing to production, getting faster feedback

*Pipeline*
`Production Pipeline: master commit -> Trigger remote build -> Publish to production URL`

*Objectives*:

* Deliver your application to the end user
* Have complete control over which version of your system is being displayed to the end user
* Use previous pipelines to protect your production environment, and check everything before going live

*@CONTRIBUTE @TODO nata.house's development flow documentation*

**Never allow direct commits into branches that are associated with environments that need to be stable, such as *staging* and *production*. Every commit to *develop* or *master* branches should be added via Pull Request, after being reviewed by another developer. Configure external tools to do this (GitHub, Bitbucket or even git hooks maybe).**

**Remember to inform which version of Node needs to be used to run your projects! You can use a specific file for that, such as `.nvmrc`, or you can just add it to your `engines` config in *package.json*.**

**Follow your projects architecture! *Any pattern is better than no pattern at all!*. No need to overthink every single aspect of your architecture, or else you won't build anything, but remember to always decide on a pattern and stick to it!**

* [nata.house's front-end architecture](https://www.notion.so/natahouse/Arquitetura-Front-end-nata-house-965bd14b72ff4444bc941053960b9ea5)

**Think critically about architecture. Follow it and understand it first, but afterwards think to yourself: could this be structured any better? Make experiments and come up with new ways of doing things, it's one of the most exciting aspects about being a programmer.**

**@CONTRIBUTE add gif or image to this section**
## 2. Git

**#neverforget [git da moçada](https://docs.google.com/presentation/d/1bStodKV1rOdAQ-8RrG4wJeRY_5RIpy_PsR9PbHci5eE/edit#slide=id.p)**

**Always use small commits, specific for each separate task you are doing. This is necessary in order to:.**

* Create a consistent history of changes in the repo, making it easy for other developers to understand what was going on at a given period of time
* Make it easier to revert specific changes if that is ever necessary
* More about this [here](https://www.notion.so/natahouse/Commit-best-practices-4f51db54000e4b93b9701931b58b58e8)
* Or in english [here](https://github.com/trein/dev-best-practices/wiki/Git-Commit-Best-Practices#examples-of-good-practice)

**Always use rebase to update your feature branches before merging into develop. This helps maintain a clear history and prevents overly complicated merge conflicts. However, be careful to NEVER rebase a branch that is being used by someone other than yourself, that could cause very difficult issues to solve.**

**Avoid creating *staging* branches that cannot be merged into *master*, try to configure the differences between the environments in places other than the source code itself. This makes your delivering process much easier and reduces the risk for conflicts drastically.**

*@CONTRIBUTE add gif or image to this section*
## 3. API Design

**Every endpoint must be documented via Swagger. Ideally this will be done automatically, but depending on the project it might be necessary to do it manually. Documentation must be considered an integral part of API development.**

**Validation. Every endpoint must be carefully validated, preferably mirroring the validation implemented on the front-end. Yes, validations should be duplicated and done both in front-end and back-end.**

**Don’t be lazy when writing your validation. It is a very important part of the system and ensures database integrity. Write specific validation for stuff like:**

* Phone/document number formats (use masks)
* ENUM inputs like ‘yes’ or ‘no’
* UUIDs

**Write and document your error handling carefully. Don’t just return error 500 any time something goes wrong, use the http status codes properly to inform your client of what exactly is going on. Even within the same status code, give proper error messages, for example: inform which fields are in the wrong format or missing in case of validation errors, inform whether it is the password or username/email that was wrong when getting an authentication error.**

*@CONTRIBUTE example of proper error handling in an API*

## 4. Web Development

**Of course, always use loading indicators to tell your user that the content is being loaded. Use loading content placeholders when loading pages, like so: **

![React Placeholder](https://cloud.githubusercontent.com/assets/691940/24140211/78406120-0e1f-11e7-9738-af2b2434c50e.png)

**Use css and not JS to display or hide information in your page! This is important for both performance and SEO, it is faster to use css and also the search engine robot must be able to assess all the content in your page, not only the part that is currently visible to the user.**

*@CONTRIBUTE Add an example of this practice)*

**Use local storage to persist user data. For the vast majority of the web apps we build, we don’t want our user to have to enter his credentials every time he wants to use the platform, so we solve this by storing his information in the browser local storage. Unless there is a specific requirement from the client that prevents us from using this approach, this should always be done!**

* Also applies to mobile apps!

## 5. React Native

*@CONTRIBUTE Please teach me the ways of RN, master...*

## 6. CSS

*@CONTRIBUTE Your CSS tips here ;)*

## 7. React Components

*@CONTRIBUTE Help us write good React code!*
