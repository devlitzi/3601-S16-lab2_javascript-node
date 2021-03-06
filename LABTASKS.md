#Lab Tasks

For lab tasks from here on out, questions that require exploration and responding to on this markdown page will be in bolded text. You should respond to them directly within this markdown file. Markdown is effectively a plaintext, lighweight markup language that is designed to be converted into HTML; more simply, it's some text and symbols you can put into a document that will turn into pretty HTML.
Tasks that specify work to do without a written response will be bulleted.
If you're ever confused about what you need to do for a given task, ask.

## Part #1: exploring the node.js project
Study the project you have cloned. Run it according to the instrucitons in the README, including running the tests. Answer the following questions by editing this file.  This will give you a chance to play with markdown.

> Protip: Using Google to gain additional knowledge or support your conjectures about how something works is great! It's important that you think about everything and come to an understanding, though, so don't use Google as a scapegoat to get the questions done quickly or you will regret it!

#####What is the purpose of app.js? Explain what happens when a user is trying to access a page "kittens", when a user is trying to access the page "petForm", and when the user submits a form on "petForm". Explain what a "route" is.

> app.js is an instance of a node.js server that handles requests from the browser and acts on those requests according to the routes defined. When a user tries to access page "kittens" our server interprets this as the request /kittens and returns the text "Page under construction!" which is directly defined within the app.js file. This is different to a reference to an html file like petForm, which redirects the user to petForm.html. When a user submits text to petForm the submit button triggers javascript code to respond to the input and logs it. A route utilizes methods such as 'get' to reach an endpoint such as a file.

#####What is the contents of the "public" folder? What is each of the html files there and how are they referenced in app.js?

> The "public" folder contains our html files, our assets (pictures in this case), our css files, and our javascript files for the website. Each html file is a different page to the website. The user is directed to each one of these sections through requests to the server: ``` app.get('/ourPage', function(req, res) ``` and the server sending the file back through the ``` res.sendFile('ourPage.html', options) ```.

#####In your project change the message that appears when the user is trying to access the page "kittens". Describe what you did and how it worked.

> We could have just switched the words that the ``` app.js ``` script was sending but instead we decided to get it to send an html file so that development had "progressed." When the browser asked for the link to ``` /kittens ``` the server now uses ``` sendFile``` rather than just ```send``` so the browser recieves that file and loads it as if it was stored locally.

#####Also change the message that a user sees when they are trying to find a page that doesn't exist.

#####Describe what happens when you submit a form on petForm page. What are the form parameters in petForm? What is the method for the form? Where is the form submission handled in the project? How are parameters extracted? How is the resulting message generated? How is this different from accessing the page petForm the first time (to see the form)?

> When you submit a form on ``` petForm ``` you submit a string and it returns your string with the string length using the method "post" In this case form submission is handled directly in the ``` app.js ``` file. The parameters are extracted by setting the input as a variable then calling that variable in the javascript. The resulting message is generated in the ```app.js``` file  using the ``` res.send ``` function. This is different because the first time that you access the page you access the ``` get ``` method, when submitting the form it switches to the ``` post ``` method and it calls a different function.

#####Where is client-side Javascript defined? Name file(s) in which it is used.

> Client-side Javascript is defined in the app.js as ``` ./clientJavascript.js ``` this is located at ``` /3601-S16-lab2_javascript-node/javascript/clientJavascript.js ``` It is used in only ``` index.html ``` and ```gpacalc.html``` .

#####Where is server-side Javascript helper file defined? Where can it be used? Add a function to it and experiment with where you can call this function.

> Server-side Javascript is defined in the app.js as ``` ./serverJavascript.js ``` this is located at ``` /3601-S16-lab2_javascript-node/serverJavascript.js ``` It is used in only ``` app.js ```  so we can call that function in that file.

#####What is the purpose of package.json file? What's in it, and what does it mean?

> The ```package.json``` file contains data that is accessible. Most of what is in there currently is dependencies, which allows different rules to apply to different browsers.

#####What's in .gitgnore file? What's the purpose of it?

> The ``` .gitignore ``` file contains the list of files. This tells git to ignore these files and not check them.

## Part #2: exploring testing

#####Find the testing file, describe where it is located and what it is testing. Run karma (the testing engine) as specified in the Readme and describe results. Do not edit any files at this time.

>The testing file is ``` clientJavascript.spec.js ``` and is located at ``` /3601-S16-lab2_javascript-node/javascript/clientJavascript.spec.js ```

#####After having set up Travis CI with your forked project, play around the page for your project (build history, settings, branches, etc) and describe at least 3 features you think would be useful when troubleshooting a broken project.

> Travic CI shows us what tests are failing for our project (pushed to GitHub). Sends notifications whether or not build is failing. You can have it build pull requests so that it can check requests before mergin.

#####What was the build status of your project right after you got everything set up? Use Travis to find any problems, and describe what failed, if anything. (Which files, what lines, why did failure occur, etc.)

> The build status is failing once we got everything set up. The file that failed is the test in clientJavascript.spec.js:14 that looks for kittens but finds NOT KITTENS!

#####Fix any problems described in the previous question. Describe how you fixed them. Push your fix to GitHub and post a link to the passing build (from build history) here.

> In this case there is already a test that checks that kittens is the answer given. We originally just changed the test so it would pass but eventually we just deleted the failing test (since it was built to fail). You can find the first one [here](https://travis-ci.org/devlitz/3601-S16-lab2_javascript-node/builds/104967173).

- Study jasmine testing syntax. Think of a Javascript function, describe its behavior by writing tests for it (this is test-driven development, or TDD). Add the function, run the tests. (Actually do this. Don't forget to commit your changes!)

## Part #3: adding a GPA calculator

- Add a page to the project (don't forget to add it to git) that has a form for letter grades and credits for three classes.

- In TDD fashion, add tests for functions needed to compute the GPA and then implement the functions themselves. Note, however, that karma doesn't work with exports, so after you have tested the functions, you would need to create copies of them that you are exporting. This is awkward and will be fixed in subsequent node setups. Also make sure to add the file that you are testing to karma.conf.js.

- Add a route to app.js to display the GPA on the resulting page.

- Add the basic html to the send so that the GPA is displayed as an html page. Don't add too much: later we will be using various libraries to take care of generating html.

- As you are working, don't forget to change drivers in pair-programming, practice TDD, write comments, and make frequent commits. As before, at the end just push all the changes to github.

