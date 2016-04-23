---
id: 11980
title: 'Git Conversation: Pull &#038; Fork'
date: 2013-06-25T13:03:41+00:00
author: Sam Matthews
layout: page
guid: http://giscollective.org/?page_id=11980
---
A confused **Sam Matthews** asking **Lyzi Diamond** a question about Github. A simple explanation of Fork & Pull project workflow.

**Sam**
  
haii
  
quick git question

**Lyzi**
  
yes

**Sam**
  
if someone wants to work on my master branch
  
what do they do on their computer?

**Lyzi**
  
hmm
  
do they have access?

**Sam**
  
i don&#8217;t konw

**Lyzi**
  
is it a shared repo?
  
or is it YOUR repo

**Sam**
  
well, I made it

**Lyzi**
  
hmm
  
okay
  
first of all
  
nobody should ever be committing to a master branch
  
you should do all work on other branches and then merge them into the master
  
just good practice <img src="http://giscollective.org/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" />
  
but beyond that

**Sam**
  
wait
  
pause

**Lyzi**
  
there are two main git models
  
yes
  
pausing

**Sam**
  
what if I&#8217;m working on a project just by myself

**Lyzi**
  
doesn&#8217;t matter
  
every feature should have its own branch

**Sam**
  
ugh
  
that seems like a pain

**Lyzi**
  
that you merge into the master

**Sam**
  
for little projects
  
but okay

**Lyzi**
  
it is a way easier way to keep track of what you&#8217;re doing

**Sam**
  
I&#8217;ll accept that

**Lyzi**
  
it&#8217;s \_good practice\_ but it doesn&#8217;t mean it&#8217;s always easier <img src="http://giscollective.org/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />

**Sam**
  
gotcha

**Lyzi**
  
okay so

**Sam**
  
so, standard dev work
  
<img src="http://giscollective.org/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />

**Lyzi**
  
there are two models for working on projects together
  
there&#8217;s the shared repository model
  
and the fork and pull model
  
the easiest one to keep track of is fork and pull
  
i prefer it
  
so basically
  
I make a repo, myProject
  
lives at github.com/lyzidiamond/myProject (not really but you get me)
  
so you&#8217;re like, i wanna contribute to that

**Sam**
  
yup

**Lyzi**
  
so you go to my repo
  
and you fork it

**Sam**
  
forked.

**Lyzi**
  
and you make your own copy
  
at github.com/sam/myProject
  
then you clone your copy to your local machine
  
work on it just like you would normally

**Sam**
  
okay
  
pause

**Lyzi**
  
add, commit, push
  
yes

**Sam**
  
so now it&#8217;s on my local machine

**Lyzi**
  
yes

**Sam**
  
anything I do to this
  
has no affect on the original project yet
  
correct?

**Lyzi**
  
nope
  
your forked version is not connected to the original
  
i mean, it sort of is
  
but you don&#8217;t have any access to the original

**Sam**
  
but, it&#8217;s a new branch

**Lyzi**
  
no
  
not a new branch

**Sam**
  
okay

**Lyzi**
  
it&#8217;s a forked project

**Sam**
  
a new project

**Lyzi**
  
yes
  
it has all the same branches as hte original project

**Sam**
  
because it&#8217;s not a shared repo

**Lyzi**
  
yes
  
it is a copy

**Sam**
  
it&#8217;s my own repo

**Lyzi**
  
yes

**Sam**
  
okay
  
aaaand
  
continue

**Lyzi**
  
okay so you make all your changes
  
and you&#8217;re like
  
&#8220;hey Lyzi, i want to integrate these changes to your project&#8221;
  
so you initiate what&#8217;s called a Pull Request
  
on my repo

**Sam**
  
and you are naturally hesitant, knowing

**Sam**

**Lyzi**
  
hahaha

**Sam**
  
okkay
  
so a pull request comes after a fork

**Lyzi**
  
well

**Sam**
  
in this case

**Lyzi**
  
a pull request comes after you fork something and then make changes to it
  
so you&#8217;ll go to github.com/sam/myProject
  
and you&#8217;ll go to the drop down
  
and be like, pull request

**Sam**
  
on my own repo?

**Lyzi**
  
yes
  
on your version of the forked repo

**Sam**
  
alright

**Lyzi**
  
remember when i said it was loosely connected?

**Sam**
  
yes

**Lyzi**
  
from your repo&#8217;s perspective, my original repo is what&#8217;s called an &#8220;upstream&#8221;
  
so let&#8217;s say you keep working on myProject, but I&#8217;m making changes to it too
  
and you want to pull down my changes periodically
  
you can do that
  
loosely connected

**Sam**
  
okay, nice

**Lyzi**
  
so once you do the pull request
  
i mean
  
initiate the pull requets
  
you do what&#8217;s called a review
  
and github is like, here are the things that you&#8217;ve changed
  
line by line
  
comparing sam/myProject to lyzidiamond/myProject

**Sam**
  
in the most current state of both

**Lyzi**
  
yes

**Sam**
  
or to the lyzi/myProject at it&#8217;s state when I forked?

**Lyzi**
  
nope

**Sam**
  
its*
  
okay
  
current

**Lyzi**
  
to the current one
  
and then you submit the request
  
and i&#8217;m like NO FUCK YOU
  
haha

**Sam**
  
haha
  
okay
  
how are you warned?

**Lyzi**
  
so once i receive your request, i can go line by line and pull the changes
  
on github

**Sam**
  
like&#8230; &#8220;you have one pending pull request&#8221;

**Lyzi**
  
yeah
  
gh has a dashboard for them

https://help.github.com/articles/using-pull-requests

this is the full version of what i just explained to you
  
including the different repo models and everything

**Sam**
  
awesome
  
so here&#8217;s my next question

**Lyzi**
  
yes

**Sam**
  
I&#8217;m editing my forked version
  
and you&#8217;re editing the master version
  
&#8220;original&#8221; version

**Lyzi**
  
yes

**Sam**
  
and I don&#8217;t know this
  
so say I edit function beardyMan();
  
but you actually delete function beardyMan();
  
and now the code works on a new function shavedGuy();
  
my merge no longer is relevant

**Lyzi**
  
well there are a couple things you can do to prevent htose issues

**Sam**
  
so do you just go, &#8220;sorry bro you&#8217;re too late&#8221;
  
and not accept my pull request

**Lyzi**
  
well
  
i could
  
but we could avoid the problem altogether
  
the things you&#8217;d do would be
  
1. before you make the pull request, pull down upstream changes
  
(using fetch and merge)

**Sam**
  
so that updates my git init direcotyr
  
to your current version

**Lyzi**
  
that updates your forked version with the changes from my original verison
  
yes
  
and this is also a prime reason why you work on feature branches
  
instead of on the master branch
  
your code will still work on the feature branch even if it doesn&#8217;t work on the master branch

**Sam**
  
ah

**Lyzi**
  
because the feature branch doesn&#8217;t know about me deleting beardyMan()
  
eventually that will have to be reconciled
  
right?

**Sam**
  
correct

**Lyzi**
  
and a best practice when working on a branch is to constantly pull in changes from the master branch
  
but yes, once i receive hte pull request i can go line by line and accept or reject changes
  
this is why git == best

**Sam**
  
and those changes will be incorporated into the master if accepted?
  
or into your branch
  
which can then go to master
  
?

**Lyzi**
  
either way, depends on what you put in your pull request

**Sam**
  
because, you don&#8217;t want to be working on the master

**Lyzi**
  
well right
  
but ideally your pull request will only have changes on a branch

**Sam**
  
well hot damn

**Lyzi**
  
i think we should play with this with some text files
  
i may do that tonight

**Sam**
  
that&#8217;s a good idea

**Lyzi**
  
set up a practice repo
  
and we can practice

**Sam**
  
gisc.github.com

**Lyzi**
  
well see because that&#8217;s a group

**Sam**
  
oh yeah

**Lyzi**
  
that&#8217;s a shared repository model, right?

**Sam**
  
yup

**Lyzi**
  
all the members have push access to all the repos
  
in that case you HAVE to work on branches

**Sam**
  
so people are just throwing eggs at a pan

**Lyzi**
  
otherwise it&#8217;s conflict city

**Sam**
  
hoping they all come from the same chicken

**Lyzi**
  
haha
  
i like that!

**Sam**
  
hah
  
it almost makes sense?
  
well, that was exactly what I was looking for
  
youdabest

**Lyzi**
  
no prob!
  
and we can get into shared repo conventions another time
  
because that&#8217;s how many many collaborative dev environments work
  
you&#8217;re constantly committing to a central codebase