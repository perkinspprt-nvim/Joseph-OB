SOME WEB BASICS :: 

Well, I'm finally starting the Odin Project. 

So far, I just doubt have to skip anything and actually read the stuff, and I'll understand the stuff. 

- [What is a web server?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Pages_sites_servers_and_search_engines)
- A computer that hosts a website on the internet. 

- [What is a network?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work)
- A group or system of people or things that are interconnected.  

- [What is the internet?](https://www.youtube.com/watch?v=7_LPdttKXPc&t=46s)
- The Internet is a worldwide network of networks that uses the Internet protocol suite (also named [TCP](https://developer.mozilla.org/en-US/docs/Glossary/TCP)/[IP](https://developer.mozilla.org/en-US/docs/Glossary/IPv6) from its two most important [protocols](https://developer.mozilla.org/en-US/docs/Glossary/Protocol)).

- [What is an IP address?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work)
- An **IP address** is a number used to address each device on an IP network uniquely.

_IP_ stands for _Internet Protocol_ which is the [protocol layer](https://docs.oracle.com/cd/E19683-01/806-4075/ipov-7/index.html) with which the address is associated.

"IP address" typically still refers to 32-bit IPv4 addresses until IPv6 is deployed more broadly.

- [What is a router?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work)
- A router is a networking device that forwards data packets between computer networks. 

- [What is an ISP?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work)
- A company that provides access to the internet. This can be through dial-up, cable, wireless, fiber-optic etc. 

- [What are packets and how are they used to transfer data?](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works#packets_explained)
- These are the small chunks through which data is transferred on the internet. 
  They are transferred this way because it is easier to recover smaller chunks in case of corruption and loss and it makes it faster if the chunks are routed through many routes. 

- [What is a client?](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works#clients_and_servers)
- Clients are the typical web user's internet connected devices. (laptop, phone, etc.)

- [What is a server?](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works#clients_and_servers)
- Servers are computers that store webpages, sites and apps. when a client wants to access a webpage, it gets downloaded from the server and displayed through the browser. 

- [What is a web page?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Pages_sites_servers_and_search_engines)
- These are any of the pages that can be displayed on a web browser (Chrome, FFox, edge, Opera, qute etc.)

- [What is a web browser?](https://www.youtube.com/watch?v=BrXPcaRlBqo&feature=youtu.be)
- This is any software that allows you to access the world wide web. 

- [What is a search engine?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Pages_sites_servers_and_search_engines)
- A web service that helps you find any other web pages. 
  (google, duckduckgo, bing, Yahoo etc. )

- [What is a DNS request?](https://www.youtube.com/watch?v=72snZctFFtA&t=45s)
- Domain Name System is a system of web page names (www.google.com. ) that helps you so that you don't have to know the IP address of the server to access the web page. The request is basically just a demand for info sent by the user's computer. 

- [Which browser are you currently using?](https://www.whatsmybrowser.org/)
- FireFox Developer Ed. 

- [In your own words, describe the process that takes place when you initiate a search on google.com in terms of what we discussed on this section.](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Pages_sites_servers_and_search_engines)
- Your computer makes a request to access the domain of google.com and thus it sends a DNS request to google's servers and and a server then sends back packets to the user contain the web page and then they are displayed to them through the web browser. 



---
## *13/11/2023 - GIT OMG, IT's GIT!!! and some other stuff* ::
Okay, I just made some SSH thing after configing the Git thing according to Odin. I have successfully attached the SSH thing. Still don't know what that means...or does. 

INTRO TO GIT : 

Git is a epic save button for files and Directories. Officially, Git is a version control system. 

A _save_ in a text editor records all of the words in a document as a single file. You are only ever given one record of the file, such as `essay.doc`, unless you make duplicate copies (which is difficult to remember to do and keep track of)

However, A save in Git records differences in the files and folders and keeps historical record of each save. This feature is a game changer. As an individual dev, Git enables me to review how my project is growing or easily `look at/restore` the previous file states from the past. Once connected to a network. Git allows me to push my project to Github or other alternatives such as; Bitbucket, Beanstalk or GitLab for sharing and collab-ing with other devs. 

Git works on your local machine while Github, is a remote storage facility on the web for all my coding projects. By learning Git, I can showcase and keep my code on GitHub (which the Odin project will also continue to use for the rest of the course.)
Git is also a pretty essential skill for modern web devs because many companies look at it as a skill that you can get employed for. 

Assignment for today : 
### [Assignment](https://www.theodinproject.com/lessons/foundations-introduction-to-git#assignment)

1. Read Chapter 1.1 through 1.4 in [this book about version control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control) to learn the differences between local, centralised, and distributed version control systems.
2. Watch [this video](https://www.youtube.com/watch?v=2ReR1YJrNOM) about what Git is and how it can improve the workflow of both an individual and a team of developers.
3. Watch [this video](https://www.youtube.com/watch?v=1h9_cB9mPT8&feature=youtu.be&t=13s) for some history on Git and GitHub, and make sure you know the difference between the two. Git is a technology used in the command line while GitHub is a [website](https://github.com/) you can visit.
4. If you haven’t yet installed Git, visit the [Setting Up Git](https://www.theodinproject.com/lessons/foundations-setting-up-git) lesson.
5. Take a look at The Odin Project’s very own [GitHub repository](https://github.com/TheOdinProject/curriculum). This is where all the lessons are stored! While you’re there, look at all our [contributors](https://github.com/TheOdinProject/curriculum/graphs/contributors) to gain an appreciation for how Git records all collaborative efforts and how GitHub visually represents this.
   
   Version control - Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. 

If you are a graphic or web designer and want to keep every version of an image or layout (which you would most certainly want to), a Version Control System (VCS) is a very wise thing to use. It allows you to revert selected files back to a previous state, revert the entire project back to a previous state, compare changes over time, see who last modified something that might be causing a problem, who introduced an issue and when, and more. Using a VCS also generally means that if you screw things up or lose files, you can easily recover. In addition, you get all this for very little overhead. ~ git-scm.com

![Local version control diagram](https://git-scm.com/book/en/v2/images/local.png)

The picture above is reference to how old version control systems worked when they were locally kept by devs. There were several problems with this way. 
- Local only; if they get deleted, they are gone.
- Version mistakes; It was easy to mistakingly add features to the wrong versions. 
- Collab problems; Especially On large projects, It was difficult to cooperate. 
- "It works on my machine. "; This is still a problem but it has reduced since the code was now no longer local only. 
  

## 14/11/2023 : Continuing the GIT version systems. I'll be faster with it today. 
![[Pasted image 20231114170106.png]]
  CENTRALISED VERSION CONTROLLED SYSTEMS. 

![[Pasted image 20231114163939.png]]

The next major issue that people encounter is that they need to collaborate with developers on other systems. To deal with this problem, Centralised Version Control Systems (CVCSs) were developed. These systems (such as CVS, Subversion, and Perforce) have a single server that contains all the versioned files, and a number of clients that check out files from that central place. For many years, this has been the standard for version control.

Down sides : 
* Servers only; If the servers are down, the none one can work collaboratively and everyone has to work with what locals they have.  
* Server Data Risk; If servers get corrupted, then everything is lost. The servers also suffer this problem of losing everything. 

DISTRIBUTED VERSION SYSTEMS: 

![[Pasted image 20231114170108.png]]


Here the data is much more secure because when the client checks and mirrors the database. They get all the versions instead of one specific one. In the case that any one of them has a problem, any other one of them can backup the servers or share their versions. 

## 15/11/2023 : Git basics. Nice 

learning basic git commands. This is going to be very fun. 

Wooooo! That was extremely fun. I learned a ton. let me just quickly log what I have learned.  

git --version : just to check the git version. They advised over 2.28. 

After getting the repo's SSH thing copied to your clipboard. use `git clone SSH_THING` to put that stuff in a repo. 

I keep my files on my mac in `/Users/joseph/repos/`. 
I cloned my repo into the repos folder. 

touched a new hello_world.txt and inside the `Odin_git_test/` directory and then used `git status` in order to see the current status. The file appears in red meaning it is not "staged". It seems that in order to *commit* your changes. you first use `git add hello_world.txt` to add hello_world.txt to the Git staging area. When you git status it. it will be green meaning it is now stages and ready to get committed. 

To commit, I use `git commit -m "Add hello_world.txt."`. The text in the quotes is a message kind of usually used to describe the commit and it's purpose. you can also use `git log` to to see the committers, time and date the commits were made and so much more information. After using vim or nvim to edit the files (`vim hello_world.txt` or `nvim hello_world.txt`). you have to then use `git add` and then commit. 

Now, In order to upload the work to Github, you need to `git push` the commits. I used `git push origin main` because we are on the main branch. however wee could have just used git push. After this, I reloaded Github and bam! there it was. This is extremely exciting. 

Git cheatsheet is linked here: [[Git cheatsheet.]]

I'll stop there for now and maybe will touch Introduction to HTML and CSS when I get home. I'll try my got knowledge by trying to git my website thing I built when I was a noob. 


## 16/11/2023  ~INTRODUCTION TO HTML AND CSS~

Elements ant Tags - HTML :                                               

HTML defines the structure of the content on the web pages. We use HTML to create ;
- paragraphs.
- headings.
- lists.
- images
- links 
- etc 

Almost all the elements in HTML are just content wrapped inside tags. You define an opening tag with `<>`. For example, a paragraph tag would Look like this : `<p>`. I can then start making a paragraph until i close the tag like this `</p>` 

Here is an example of a paragraph in HTML. :
```html
<p>some text content</p>
```
Of course there are tags that are exceptions to the rules and basically don't have a ending component. This is usually because they don't usually wrap any content. 
EX : 
```html
<br>
<img>
```
Assignment is to watch Kevin Powell's Intro to HTML. 
Links : https://www.youtube.com/watch?v=LGQuIIv2RVA&list=PL4-IK0AVhVjM0xE0K2uZRvsM7LkIhsPT-

Notes :

HTML is a hyper text language meaning it can link to other things. Very simple language made up of Tags.  


## 17/11/2023 ; HTML  Boilerplate

 All the HTML files have some boiler plate (not very useful stuff) that you need to place inside your file. We will look at using that Boilerplate in HTML and also opening the File in a Browser. 

When making a website. The "Homepage" File should usually be index.html. This is because that this is what the website defaults to. 

Old HTML used some long boilerplate but the current uses `<!DOCTYPE html>`and it will also generate a html end tag </html>

Time to put some tags 

1. `<!DOCTYPE html>` *this specifies the use of HTML 5*
2. `<html lang = "en">` *lang is an attribute that *
3. `<head> </head>` This is where the meta data of the files go. (the files that don't have elements of a webpage.)
4. `<body> </body>` Where most of the web page components are placed. 

## 17/11/2023 ; Working with text. 


## 20/11/2023 ;
Working with text : 

Sorry, I haven't seen y'all in a long time. I fell of my program schedule and I don't feel the happiest about it. I have some tests and other goals for today but I will manage to at least finish a topic or two. 


- How to create paragraphs.
`<p> </p>` 
The paragraph tags separate text into paragraphs. 
```html

<html>
  <head>
  </head>
  <body>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua.</p>

    <p>Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
  nisi ut aliquip ex ea commodo consequat.</p>
  </body>   
 </html>

```



- How to create headings.
`<h1></h1>, <h2></h2>` This sequence continues till h6 as they continue to reduce in size. 
```html

<html>
  <head>
  </head>
  <body>
    <h1>This is a heading 1</h1>
    <h2>This is a heading 2</h2>
    <h3>This is a heading 3</h3>
    <h4>This is a heading 4</h4>
    <h5>This is a heading 5</h5>
    <h6>This is a heading 6</h6>
  </body>
 </html>

```

- How to create bold text. :
We use the `<strong>` element as it makes the visibility and thickness of the text stronger. it is often quite nested in other HTML tags. 

- How to create italicized text.
Here, we use the emphasized tag, `<em></em` which italicizes the the text put within it. 

- The relationships between nested elements.
  You may have noticed that in all the examples in this lesson we indent any elements that are within other elements. This is known as nesting elements. When we nest elements within other elements, we create a parent and child relationship between them. The nested elements are the children and the element they are nested within is the parent.

- How to create HTML comments.
<!-- I am an HTML comment -->. This the format for making HTML comments. as expected, They are ignored and not run 

LISTS : 

Hmm, I'll just do 2 topics today. 

Making Ordered and Unordered Lists : 

#### UNORDERED LISTS : 
This is for unordered Items. We have like shopping lists where Order doesn't matter. We use the <ul></ul> tag and make sure to use the <li></li> element to define the elements of the list. 
 ```html
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```
Every list item begins with a bullet point if it is an un-ordered list. This is not the same for ordered lists. 

#### ORDERED LISTS :
Ordered lists are Put within the tag <ol></o> and they use the same <li></li> list elements. Ordered lists however are numbered. 

```html
<!DOCTYPE html>
<html lang="en">

  <head>
    <meta  charset="UTF-8">
    <title>Experimenting with Lists. </title>
  </head>

 <body>
    <h3>MY TOP 5 MOVIES OF ALL TIME : </h3>
    <ol>
      <li>The passion of Christ. </li>
      <li>Interstellar. </li>
      <li>Fight club</li>
      <li>Batman(2022)</li>
      <li>The Dark Knight.</li>
    </ol>
    <p>
      I watched these movies a while back and I think that they made me who I am.
    </p>

 </body>
</html>
```

#### Links and Images. 

Links are one of the key features of HTML. They allow us to link other HTML pages. This is what makes the web the web. You will be learning how to create links and add some visual flair to our websites by embedding images. 

#### Creating links to pages on other websites of the internet. 

I'll focus on this and finish up for today. then continue on Links and images tomorrow. 

In order to use a link another website. I have to use the anchor tag <a></a>. I have to use what is called an attribute of the element which is href(hyper-text reference.) with this I can make like a Text that if you click it, it will redirect you to another site. 

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8"> 
    <title>Links and the Web. </title>
  </head>
  
  <body>
    <h1>Homepage. </h1>
    <a href="https://www.theodinproject.com/about">The Odin Project : About</a>

  </body>
</html>
```

I have to take new approaches to note taking this stuff. 



25 Nov 2023.
Hello, I am here to do the Odin project after not doing it for a while. The notes are going to get relatively shorter compared to how they were in the beginning. 

- <a></a>anchor tags are used to define links and the href attribute is used in order to define where the anchor will redirect you to. 
- To link to another website, you just add the href attribute and the link. <a href="https://www.website.com"></a>
- In order to make it that the link will open in a new tab, you need another attribute called target. 
- set target="_blank" and it will open in a new tab. 
- There is another attribute that was used and that is used to define the relationship between the current page and the linked page. 
- The `noopener` value prevents the opened link from gaining access to the webpage from which it was opened. The `noreferrer` value prevents the opened link from knowing which webpage or resource has a link (or ‘reference’) to it. It also includes the `noopener` behaviour and thus can be used by itself as well.
  ```html
<a href="https://www.theodinproject.com/about" target="_blank" rel="noopener noreferrer">click me</a>
```
- Generally, there are two kinds of links we will create:

- Links to pages on other websites on the internet.
- Links to pages located on our own websites.

#### Absolute links

Links to pages on other websites on the internet are called absolute links. A typical absolute link will be made up of the following parts: `protocol://domain/path`. An absolute link will always contain the protocol and domain of the destination.

We’ve already seen an absolute link in action. The link we created to The Odin Project’s About page earlier was an absolute link as it contains the protocol and domain.

`https://www.theodinproject.com/about`

#### Relative links

Links to other pages within our own website are called relative links. Relative links do not include the domain name, since it is another page on the same site, it assumes the domain name will be the same as the page we created the link on.

Relative links only include the file path to the other page, _relative_ to the page you are creating the link on. This is quite abstract, let’s see this in action using an example.

Within the `odin-links-and-images` directory, create another HTML file named `about.html` and paste the following code into it:

#### Images:
The internet would be some what boring if we couldn't view pictures from time to time. HTML provides the ability to source some images. 
- We commonly use relative paths to link images (This means that the images has to be somewhere in or below in the file directory).
- We use the <img> tag and also have a src attribute pointing to a relative path. 
- you can set width and height for those as well. 
  
  Here is the link to the Github commit I made for this :
  [Github link : links and Images](https://github.com/perkinspprt-nvim/Odin-sidework/tree/main/Odin-links-and-images)

### PROJECT ODIN-RECIPES
I will review this one after I'm done with the work. I seem to work faster that way

Here is the Github link to my repo;
[Github repo for Odin-recipes](https://github.com/perkinspprt-nvim/odin-recipes)

Also the link to the live website thing (Just learned about it) : [My live preview page for Odin recipes.](https://perkinspprt-nvim.github.io/odin-recipes/)

Well, I did a lot. I added three recipes to the project and they were all quite lengthy. I used allrecipes.com for the data (Thanks so Much). I think that. I can say I applied it really well and I am excited to see what I can add-on with CSS when I learn it next unit. 

Hey loser, you haven't been doing the work lately huh. 
Let us finally work on touching some CSS. 

## CSS Basic syntax
At the more core of CSS, 

it is divided into a selector, which more or less just allows to pass specific CSS to specific tags and bit of the HTML. 

We have the property which is a property of the HTML, kinda like a variable and we assign a value to it so that the property can be changed accordingly.  

In CSS, a lot of the times, a wrapper class is needed which is the div. The dic is inherently empty and thus is mainly just used to package code. 

- " * " is the universal selector and will select elements of all types. 
  ```css
* {
  color: purple;
}
```

- Type selectors (element selectors) will select all elements of the given element. If the css is selecting Divs, then more or less all the Divs will be affected by the CSS. 
  
- Class selectors; These are selectors that I can add as an attribute to an HTML element to so that I can then use it as a selector In CSS. 
  
  ```html
<!-- index.html -->

<div class="alert-text">Please agree to our terms of service.</div>
```

```css
/* styles.css */

.alert-text {
  color: red;
}
```

Cannot be separated with whitespace and have to be referenced with " . "

- The way I say it, there are class selectors that are used to classify and apply the CSS effects In mass. This seems to be cross element (affects tags that aren't the same).
- Then there are id's. They are pretty individual to one thing so they shouldn't be repeated. Just like you really only have one title. 
  ```html
<!-- index.html -->

<div id="title">My Awesome 90's Page</div>
```
- id's use the "#" hash and the classes use the "." dot in order to specify the selector in the CSS. 

GROUP SELECTOR : 
you can use the group selector in order to apply the same CSS properties to some specific selectors and even later. 
```css
.read,
.unread {
	color : white;
	background-colour : black;
}

.read {

}

.unread {

}
```

Well, I have been doing my css exercises and lately I have been having fun doing the work. I then want to do some personal projects real soon and also study some physics, I'm going to study physics after reading for a bit and then later do some More coding. 

Today, I plan to get done with the foundations of the CSS exercises. after that, some physics catchup and then hopefully also do what I have to do today. 






