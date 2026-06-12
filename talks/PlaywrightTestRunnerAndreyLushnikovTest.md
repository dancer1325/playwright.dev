https://www.youtube.com/watch?v=QKOQeXWy7DM

* goal
  * new Playwright Test Runner

* Playwright Test
  * == cross-browser web testing framework /
    * written | Node.js
    * open source
    * sponsored -- by -- Microsoft
    * run tests in parallel & isolated
    * flexible & customizable
  * why to create ANOTHER Test Runner? 
    * test runners | JS,
      * ⚠️are UNIT test runners⚠️
        * ❌!= E2E test runners❌
        * ❌NO require❌
          * support cross-browser

TODO: 
* So let me hop to my terminal and I will create a new folder
* And I will start from scratch and initialize a new npm project
* Now let's do npm init PlayWrite
* And what this does is actually sets up this project to use PlayWrite for me
* While doing so, it will ask me all kinds of different questions
* For example, what language do I want to use to author tests? And it is TypeScript because I actually don't need to set up anything additional, I can just author my tests in TypeScript and they will be transpiled to JavaScript and run seamlessly, no need to do Babel and Webpack or anything
* It will ask me where to put my tests, of course I want to have a GitHub Actions workflow, and yeah, examples are good
* So now once I answered all the questions, it installs all the dependencies for the NPM, downloads all the browsers, I have them downloaded already so these have been reused
* And now I am here with a bunch of sources pre-created for me
* Let's look into these sources
* First we have this example end-to-end test.

2. Playwright Test Runner: Features and Configuration

04:09
Short description:
The Playwright Test Runner allows you to write tests using just a few lines of code. It provides a well-isolated test page for each test, ensuring no clashes between pages or state. You can navigate the test page to a specific website, locate elements, and interact with them. The configuration file allows you to set up different environments, such as running tests in different browsers. The Playwright Test Runner supports cross-browser testing, device emulation, and parallel test execution out of the box.

It is just seven lines of code and let's pretend that we don't know what Playwright is, let's just read it. So first line we import something, test and expect from the package we just installed. Now test turned out to be a function and we use it to create a test. We give it a basic name and we pass in a callback which is actually a test body. Interestingly as an argument in the test body, we have this page that comes from the Playwright test framework. This is a well isolated test page that is different for every test and no tests have pages or state clashing. So this is the isolation we talked about. This is a browser page so we can navigate it to a certain website and then we can locate an element using a text on the page and after that we can click what you located. And everything is async so we wait for it to complete. It looks like it does some kind of navigation so after this we can expect the page to have a certain title like getting started regex. Pretty transparent.

OK what else do we have? We have this configuration file. This time I will actually use Wim to go into it. Now this is a generated file and it has lots of comments so you can easily go through it and understand what's going on. We don't need any of this stuff. I want to focus on this projects array. Now projects are kind of environments. We have only one test and we want to run this test in different browsers like Firefox or in Chrome and this is what projects are for. So here we have five projects pre-setup for us. We have Desktop Chrome, Desktop Firefox, Desktop Safari. All good. And we even have mobile emulation for Pixel 5 which is Android and iPhone 12 which is a Mobile Safari. So we have one test and five projects which means we'll run five times for this test. Let's see how this actually happens. So to run tests I can do mbxplaywrite test and as I run this command it runs five tests using five workers. So we will write that it actually runs five tests which is nice. But the other important thing is that it actually uses five workers. So all of these test runs are happening in parallel and actually only take eight seconds which is pretty fast. OK so out of the box we didn't do anything. We already got cross browser test runs, we got device emulation and we got parallels.

3. Running Tests in Parallel and Code-Gen

07:17
Short description:
We can run tests in parallel, customize the output with different reporters like Allure, HTML, and JUnit. Playwright has a simple and intuitive API to control different browsers. We can also use Code-Gen to generate code and interact with web pages.

We can run these tests in parallel on our powerful machines, which saves a lot of time. There are various reporters available for customizing the output, such as the line reporter for an interactive terminal prompt or the HTML reporter for visual results. By default, the tests run with a line reporter, but we can also generate an AllureReport using a third-party AllureReporter. Playwright provides a simple and intuitive API to control different browsers, and we can use different reporters like Allure, HTML, and JUnit.

Now, let's do a quick recap. We can install Playwright into projects using the npm init playwright helper script. Once Playwright is installed, we can run tests with npx playwright test, and it will run in parallel. The Playwright API is straightforward and allows us to control all different browsers. We also have options for generating reports like Allure, HTML, and JUnit.

Next, let's talk about Code-Gen. We can use the command 'npx playwright code-gen' to generate code and save it to a file. This opens two windows, a regular browser window, and the Playwright Inspector. The Inspector has a record button that allows us to record interactions with the web page. We can navigate to different pages and keep interacting with them.

4. Using Playwright Test Runner and Code-Gen

08:57
Short description:
We can install Playwright into projects using npm init playwright helper script. Once installed, we can run tests with npx playwright test. Playwright provides a simple and intuitive API to control different browsers. It supports various reporters, including LUR, HTML, and JUnit. Now, let's explore a new feature called Code-Gen. By using mpxplaywrite code-gen, we can generate code and interact with web pages. The generated code can be used to navigate web pages, interact with elements, and perform actions. We can also run the generated script to verify its functionality.

So we can create install playwrights into projects with this npm init playwright helper script. And once we have playwright installed, we can actually run tests with npx playwright test. And it all runs in parallel. And this is what playwright actually looks like. It's very simple and intuitive API. And this is a single API to control all of the different browsers. And of course we have reporters, we have a LUR report, we have HTML report, we even have the JUnit report if you're into this kind of stuff.

Okay, so we just played with how do we get started. Let's author some new tests. And now I want to show you a new thing which is called Code-Gen. For this, let me clear my screen. I'll do mpxplaywrite code-gen and I'll save the results of what I will generate to github.spec.gs. As I do so, two windows are being opened. The first window, the browser window, is just a regular Chrome window, while the second one is this Playwright Inspector, and we'll talk about it a little bit later, and it has this gloomy red record button highlighted. Now, everything that I do inside the browser is actually recorded by the recorder, and I just navigated to Microsoft, and I have this page code navigation. So I can actually keep interacting with my web page. I can say Playwright, wait for it to search, hit the Playwright button. Actually, on the web page I have this black box with white text underneath my cursor. So this shows me the selector that will be used as I will interact with the page. So I'll hit issues, and I'll just keep going. Let's click on Pawel. This is good enough. I can turn off the recording and quit my browser. Now, let's see if we actually have things recorded. We have our script, which is good. But does it work? So, to make sure that it actually works, I can run just this github file, and this way I actually filter by filename. But we have multiple projects. I don't need them for now. I just want to run in desktop chrome, for example. And I actually want you to see how it's been run.

5. Debugging Tests with Playwright Inspector

12:11
Short description:
In a headed mode, the script progresses in the browser window and completes in 8 seconds. Authoring a new test with Codegen is easy, and debugging is simple with the dash dash debug command. The playwright inspector UI provides source code, execution control, and action logs.

So, I want to run it in a headed mode. And this is the browser window. It goes, navigates, and this is how the script progresses. And finally, it completes in mere 8 seconds. Pretty fast.

OK. So it is really easy to author a new test with Codegen, and if I want to change something, I can always go and hop into my editor of choice and change certain lines here and there.

Now, let's pretend that this test actually does not work. How do I debug it? Well, it turns out it's pretty easy. I can just say, dash dash debug for my test. And again, it will open two windows for me. This one is a browser window that will run this test. And I will resize it to uncover the second window, which is a playwright inspector window. So I didn't have the opportunity to show you around this playwright inspector UI, so here I am. Let me show you around. We have four parts of this UI. In the very center we have this source code of the test that you're debugging. And we have a highlighted execution line, which is actually paused on the current playwright position. I can control this execution line using the control panel here. For example, I can click step over to step over this command. And as I step over the navigation, the playwright page in my browser navigates. Down below here I have the log of all the actions that the playwright is actually doing. I can see the page go to succeeded. There is a green check mark. It took just two seconds. And we're doing page click, and we're paused. And you can expand these actions and see what's actually happening inside. And page click is already pre-expanded for me. And I can see all kinds of stuff that's happening here. And, for example, playwright was waiting for element to be visible, and enabled, and stable.

6. PlayWrite Test Runner: Debugging and Tracing

14:32
Short description:
The auto-weighting feature ensures that all clicks are happening accurately. The selector playground allows for easy selection and exploration of elements on the browser page. PlayWrite Inspector provides a comprehensive UI for test debugging. PlayWrite tracing enables deep diving into browser internals, console, network actions, and page DOM after each test action.

And it scrolls into the view, and it does all kinds of stuff. And this is the auto-weighting that's built-in, and this is how we actually make sure that all your clicks are actually happening for reals. We even make sure that the element receives pointer events in a certain location. And this is where we are about to click, and you can see this location in the browser window marked as a red dot. So this is where we are aiming right now.

Okay. So last but not least, we have this fourth section which is a selector playground. And it is currently highlighting this placeholder, find the repository. This is the selector that will be used for the action that is paused right now. I can change this and say, for example, text equals TS lib. And as I change and type different selectors here, elements are being selected in the browser page. And this is cool, but this Explore button is even more cool. So as I click it, the Chrome window will activate. Bam! Now, as I hover over the different parts of the page, I can see different selectors here in this black box underneath my cursor. And as I click on this element, for example, the selector is being pasted into this input field. So I can further refine it, for example. Or I can just copy it and paste it into my editor. And this is PlayWrite Inspector, and this is how we debug tests in PlayWrite. Let's go back to our presentation.

So we just saw how we can generate tests with MBX PlayWrite CodeGen. And we saw PlayWrite Inspector, which is as easy to open as passing the "-debug flag to your command. And once you do so, you are presented with this beautiful, gorgeous UI that shows you everything you need to know about your test. Okay. So this all is very cool, but this all happened locally on my machine. Which means the test was failing locally and I had a very nice repro. I can reproduce the failure and I can debug it using PlayWrite Inspector. But what would I do if this failure would actually happen somewhere in the cloud and I would not have any way to reproduce it locally? Of course, I can take a screenshot, or for example, record a video of the whole run. But wouldn't it be cool if I can actually deep dive into the browser internals, into the browser console or network actions? Or, you know, go and even maybe deep dive into the page DOM? After each action of my test execution. So it turns out this is actually possible. And this is possible with something called playwrite tracing.

7. Playwright Tracing: Exploring TraceViewer

17:47
Short description:
Playwright tracing is a unique type of artifact that is more capable than videos and screenshots combined. It consists of trace.zip files, which are portable file formats containing all the information about the test run. TraceViewer is a program bundled with playwright that allows you to explore trace files. Additionally, Trace.playwright.dev is a website where you can drop traces and view them. In a demo, the speaker shows how to open a failing trace file and explores the features of TraceViewer.

So let me tell you about playwrite tracing. But before we actually talk about tracing, a little bit of terminology. So first things first, we call this term post-mortem debugging. Because this is a debugging of a test failure that happens somewhere far away. And there is no basic way for me to reproduce it locally. So to debug this kind of failures, and these are very nasty failures. We usually use things such as test artifacts, which are any byproducts of test running. Things like logs or screenshots of videos, all of these actually count as test artifacts.

Now in Playwright, we actually have this unique type of artifact, which is called tracing. And it turns out that tracing by itself is much more capable than both videos and screenshots combined. So let me explain you what it is and I'll show you how it works. So playwright tracing is this technology that consists of two parts. First is this trace.zip files and these are actually the artifacts. And this is a portable file format that has all the information about the playwright test run, such as actions, events, screencast, network log, console log and DOM snapshots for each of the actions. And then we also have TraceViewer and TraceViewer is this program that is actually bundled with playwright that lets you look into this trace files and explore them. And since playwright v.1.17, we even have Trace.playwright.dev, a special website where you can drop all the traces and it will be presented to you.

So let me actually give you a demo of what it looks like. So here I conveniently have a repository created specifically for this presentation. But here in this repository I have an action and it is failing. So let's explore. So for some reason something is, is been timing out and it even tells me go and open show trace. So let me actually do this. I'll go to summary and in GitHub actions we have all the artifacts uploaded, and if you actually use a GitHub action that we can pre-configure for you it will upload all the artifacts automatically. So I can just download this this trace file. I have it here, unzip it, and this is the trace file and I'll use this trace.playwright.def file and I will just get this trace and drag and drop it over the area. This is the trace URUI. So a lot of stuff is actually going on here, so let me show you around. Up here we have a timeline and you can hover over the timeline and scrub over it to see how things are happening inside your web page. This is pretty much like a screencast but the screencast is actually overlaid with all the actions like these bars above the screencast. These are the actions.

8. Using Traceviewer and Playwright Test

21:25
Short description:
In Traceviewer, I can see the navigation, clicks, expects, and other actions in my script. The panel on the right provides information about each action, including console messages and network activity. The Dom Snapshot allows me to interact with the real HTML and CSS of a page. I can scroll, type in input fields, and inspect the DOM using DevTools. Traceviewer is a powerful tool for debugging and analyzing test actions. If you're interested, visit trace.playwright.dev for a beautiful UI and more features. Playwright Test offers installation with npm, test authoring with code.gen, debugging with inspector, and post-mortem debugging with tracing. Check out our documentation and join our social channels for more information.

So for example up here, I can see that navigation took something about 600 milliseconds. This blue line is a page that goes to call and so on I can see here's a click, here's some expect, here's another click, and so on.

Now on the left hand side I have the list of all the actions in my script in a chronological order and This is actually keyboard navigable. I can go up and down to select different actions and For each actions on the right hand side. Oops, sorry I have this panel with all the information about this action and I have all the console messages that are happening during this action run and And even all the networks that's happening here Right.

So navigation is obviously very heavy on network And in the middle here We have a Dom Snapshot. So this thing is not a screenshot It's snapshot, which means it's a real HTML real CSS. You can scroll it. You can even you know type Into input fields. There is no JavaScript, so it will not react but other than that CSS hovers all of the stuff works and You can even go and inspect it with DevTools So here I am I can use DevTools to look into the DOM of GitHub Which is very nice and it gives me limitless capabilities now for clicks and With Navigations, we like all of these actions we have here and Well last but not least we can see that this last one page click we tried to click on something called wolf and This action timed out so well, honestly, there is no wolf on this page. So it's very predictable This was Traceviewer

So, please use trace.playwright.dev it's a very nice website and once you do you'll have this beautiful UI with all the goodies and bells and whistles that I showed you and This is it for this presentation recap

So playwright test Well, first of all, you can install it with npm playwright You can author new tests with code.gen You can debug your tests with inspector and you can do post-mortem debugging with tracing so If you use playwright test, you are basically covered in all your live stages as a test author If you like what you've seen Please head over to our documentation to learn more about playwright We are also present on social channels. Please Join our slack.