# Software Projects

**Don’t use strings directly in your source code. Abuse declaring constants, in a separate file if they are going to be shared across the system or at the top of the file if it is to be used only once.**

*@CONTRIBUTE examples*

**Always consider using internationalization tools such as i18n, even if the app doesn't immediatly need to be multi language, because:**

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