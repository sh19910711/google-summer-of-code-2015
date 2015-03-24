# Create Web Console Browser Extensions

## Project Description

The web-console is a debugging tool for Ruby on Rails applications.
In order to debug web applications interactively, it provides an interactive Ruby session to the developers.
The console will be displayed in the current page of the browser,
and the session has the context of the view or the controller actions,
so the developers can debug their application in the target context of the source code via its console.

The goal of this project is to create the browser extensions of web-console.
For example, it allows to display the console aside from the web application's view (e.g, in the developer tools of the browsers)
By doing this, the console can be displayed without breaking affects to the view code of the web application,
and the developers could use the console by just installing the browser extension.

And the other thing, the extension can show the information of models and routes of the context of the current page in the browser.
It is also useful to debug web applications effectively.

### Why did you choose this idea?

I have some experiences of the browser extension projects,
so it fits with my knowledge and skills.
The project makes the web-console loose coupling from the Rails applications,
it is important to debug applications without extra effects.

### Please describe an outline project architecture or an approach to it

web-console is displayed by calling console() method from a view or controller.
For example, the developer need to add a line such as "<% console %>" to the view in the case of using ERB.
I think the similar switch is needed for the browser extension.
My idea is to add "X-WEB-CONSOLE" to the HTTP response headers when web-console is enabled.
In other words, if the web-console is enabled, the web application always returns "X-WEB-CONSOLE: true" as HTTP headers.
And the browser extension is enabled only if the web application returns "X-WEB-CONSOLE: true" as its response header.
In order to inject that HTTP header, I will extend WebConsole::Middleware for that in the web-console repository. It will be a small change.

About the Browser Extension, I will develop a chrome extension as prototype at first.
When the feature forms concrete shape,
then I will create Safari Extension and Firefox Extension have same behavior of the Chrome Extension.
To keep the software simple, Browser Extension show web-console's view only.
When the browser opens another page, the console view is also reloaded automatically.
The developers can install the software by manually or by finding from hosting service (e.g, Chrome Web Store). 

![Rough Design of Extension](http://farm8.staticflickr.com/7595/16692019960_1f7b39758b_b.jpg)


### Give us details about the milestones for this project

Here is a timeline:

// 28 Apr. - 24 May

Milestone #0 - Community Bonding Period

* Brush up the feature and architecture of the software
* Find and fix issues of web-console
  - I will keep to do it in the whole terms

// 25 May - 25 Jun.

Milestone #1 - First-Term

* Support Custom HTTP Header on web-console
* Create Chrome Extension (as prototype)
  - Show console view as devtool panel
  - Add feature to reload console view on change page
* [Extra Task] Find Cross-Platform Browser Extension SDK or Library


// 26 Jun. - 16 Aug.

Milestone #2 - Second-Term

* Support Firefox
* [Extra Task] Support Safari
* Release Software


### Why will your proposal benefit Ruby on Rails?

Not only display console, the browser-extension will have potentials to add
more useful supports of web-console.

### Please describe any previous Open Source development experience

Here is a brief information:

- social-snippet (Ruby) # Working in Progress Now

  This is my open source software written in Ruby.
  It is a snippet manager for programming competitions.
  * URL: https://github.com/social-snippet/social-snippet
  * URL: https://social-snippet.github.io
  * Sub Projects: https://github.com/social-snippet

- duck-lang (C, Language)

  A simple scripting language based on the idea of duck-typing.
  I have added some language-syntax and tests.

  * URL: https://github.com/gregtour/duck-lang

- git-contest (Ruby, Git)

  This is my open source software written in Ruby.
  It is a Git extension for programming competitions (e.g, Google Code Jam).
  * URL: https://github.com/sh19910711/git-contest
  * Poster: http://docs.yomogimochi.com/ruby-wc/1414904336-git-contest.pdf 

- git (C, Git)

  Git is a free and open source distributed version control system.
  I added small improvement [1] of git-fsck command.
  * URL: http://git-scm.com/
  * Commit: https://github.com/git/git/commit/effd12ec876df016d4346fee0d3d6bf31308fa11

- tilt-fs (Ruby)

  This is my open source software written in Ruby.
  It is a userspace filesystem based on Tilt.
  * URL: https://github.com/sh19910711/ruby-tilt-fs

- search-plus (Chrome Extension)

  This is my open source software (WIP).
  It can find all tabs you're looking for.
  * URL: https://chrome.google.com/webstore/detail/search-plus/cdpohbejnbclggljmoijjcpdhbaaijfm
  * URL (WIP): https://github.com/sh19910711/crx-search-plus

- Scrimmage/karma-slim-preprocessor (JavaScript, Testing)

  Karma Plugin to compile slim to html on testing.
  I added supports for command-line options.
  * PR: https://github.com/Scrimmage/karma-slim-preprocessor/pull/3
  * URL: https://github.com/Scrimmage/karma-slim-preprocessor

- Other Projects and Activities

  * GitHub: https://github.com/sh19910711
  * RubyGems: https://rubygems.org/profiles/sh19910711


### Why are you interested in Open Source?

It leads to well designed software.
Accumulated things by open source are not only source code of software but also approaches how to create software.
There are many things to learn from open source.
For example, I like testing software, and I have been learning many things about testing from open source.

### How long will the project take? When can you begin?

It will take a month to create prototype as Chrome Extension,
and also take a month to support other browsers.
I can start as soon as the end of May.

### How much time do you expect to dedicate to this project? (weekly)

I can dedicate 40 hours a week for the project.

### Where will you based during the summer?

Aizu-Wakamatsu, Japan.

### What timezone will you be working in and what hours do you plan to work?

I'm at JST, which is UTC+09:00

### Do you have any commitments for the summer? (holidays/work/summer courses)

No.

## Other

### Have you ever participated in a previous GSoC? If yes, describe your project.

No.

### Have you applied for any other 2014 Summer of Code projects? If yes, which ones?

Yes, I applied to Git in the last year.

## Why did you apply for the Google Summer of Code ?

I'm new to open source, but I would like to work with open source,
since open source software helps my programming activities a lot.

## Why did you choose Ruby on Rails as a mentoring organisation?

I like web development by Ruby, and Ruby on Rails is one of the most popular web framework in the world,
so there is no reason not to try to contribute it in this summer.

## Why do you want to participate and why should Ruby on Rails choose you?

I want to participate GSoC because I have to earn money to live as a student.

