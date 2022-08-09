# Angular Overview

## Learning Goals

- Give an overview of Angular.
- Describe SPA, Reactive Applications.

## Introduction

> Angular is a JavaScript framework (that also supports TypeScript) that allows
> developers to create *reactive, *single page web applications\*.

There is a lot in that one sentence, so let's break it down:

1. A _web application_ is an application that runs inside a web browser, such as
   Chrome, Safari, Internet Explorer, ...
2. A _single page_ web application is one where the browser loads an initial
   page and the rest of the interactions are handled within that page instead of
   asking the browser to reload the entire page. We'll discuss this aspect in
   more detail below.
3. A _reactive_ web application is one where each interaction is either handled
   on the client side (i.e. by code that is executed by the browser without
   needing to go back to the server) or by making requests to the server side
   _in the background_.

> Even though Angular is a "JavaScript" framework in the sense that it uses
> JavaScript in the browser to enable its functionality, Angular actually
> defaults to using TypeScript for its programming needs, and compiles it to
> JavaScript when it packages up an application to get it ready to run in the
> browser.

## Single Page Application (SPA)

To understand SPAs, we need to take a step back and look at how a browser loads
an `HTML` page and what role JavaScript plays in that.

Without SPAs, the usual lifecycle of a static web page looks like this (in a
simplified sequence):

1. The user stars a browser, which is an application that knows how to read and
   render `HTML` and `CSS`.
2. The user enters a URL in the browser's address bar that tells the browser
   which server on the internet to make a request to.
3. The browser sends an `HTTP` (or `HTTPS`) request to the server
4. The server responds and returns the `HTML` and `CSS` code that it wants the
   browser to render
5. The browser interprets the `HTML` and `CSS` code and renders the page
   accordingly
6. The user clicks on any of the links on the static page
7. The browser gets an instruction that tells it to replace the current URL with
   the URL of this new link and to start the lifecycle again at step 2.

The above is for a static page that does not have user interactivity, which is
not very common or useful. JavaScript is a way to add user interactivity to a
static page. With JavaScript, the lifecycle of the page is the same except that
in addition to being able to click on a link, the user can actually enter data
in form elements and click on buttons to give the web page (which is now an
interactive application) information and instructions. That lifecycle looks like
this (in a simplified sequence):

1. The user stars a browser, which is an application that knows how to read and
   render `HTML` and `CSS` and knows how to interpret `JavaScript`
2. The user enters a URL in the browser's address bar that tells the browser
   which server on the internet to make a request to.
3. The browser sends an `HTTP` (or `HTTPS`) request to the server
4. The server responds and returns the `HTML`, `CSS` and `JavaScript` code that
   it wants the browser to render and interpret
5. The browser interprets the `HTML` and `CSS` code and renders the page
   accordingly
6. The browser interprets the `JavaScript` code and executes its instructions
   accordingly
7. The user clicks on any of the links on the static page or interacts with the
   interactive aspects of the page
8. Either:
   1. The browser gets an instruction that tells it to replace the current URL
      with the URL of this new link and to start the lifecycle again at step 2.
   2. The browser gets an instruction through the `JavaScript`-based interactive
      part of the page and executes that instruction, which may result in a new
      URL being loaded or in some other action on the current page

The 2 interaction models (static web page vs SPA) are illustrated in the
following diagram:

![SPA Interactions](https://curriculum-content.s3.amazonaws.com/java-mod-8/ng-spa-interactions.png)

As you can see from the magenta lines, the main difference with a Single Page
Application is that it does ask the browser to reload the entire page (i.e. it
does not request a brand new URL). Instead, it requests data from the server and
uses that data to update the content on the existing page.

## Reactive applications

In the context of SPAs, reactive web applications are applications that have the
ability to make those "data requests" we discussed in the previous section in
the background. This means that the user interface presented by the browser on
the current page is still available for the user to interact with, while the
browser waits for the server to return the requested data. When the requested
data is eventually returned, the browser then updates the web content
accordingly.

A "reactive" web applications takes advantage of the browser's ability to make
"asynchronous" requests, which means that the browser is able to send a request
and not "wait" for a response. Instead, it sends the request, and continues with
whatever other work it has to do. When the server is ready to send the response,
it does so and the browser recognizes what the response is for and processes it
at that time.

Here is a high level diagram to contrast "blocking" and "asynchronous" (also
called "async") requests:

![Blocking vs Async](https://curriculum-content.s3.amazonaws.com/java-mod-8/ng-blocking-vs-async.png)

Angular provides a framework for handling the various aspects of managing a SPA,
handling user interaction and server data through async requests to make the SPA
reactive, and a host of other concerns that comes with complicated web-based
applications.

Let's learn the basics of how to work with this framework, so that we can then
dive into the various aspects that it allows us to manage.

> The versioning around `Angular` can be confusing because there is `AngularJS`
> (aka `Angular 1`) and since version 2 Angular has been referred to as simply
> `Angular` followed by the version number. The main thing to understand is that
> since `Angular 2`, a) Angular has dropped the `JS` from its name and b) it has
> been very backwards compatible and the changes have been incremental.
