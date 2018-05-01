# Web Crawler 🕷

[Brief](#brief) | [Plan](#plan)

---

I'm gonna write me a web crawler in Go!

I'd like to write the whole thing with no external packages. For testing, I used [Assert](https://godoc.org/github.com/stretchr/testify/assert).

_def: A Web crawler, sometimes called a spider, is an Internet bot that systematically browses the World Wide Web, typically for the purpose of Web indexing (web spidering). Web search engines and some other sites use Web crawling or spidering software to update their web content or indices of others sites' web content._

### <a name="brief">Brief</a>

Write a simple web crawler, limited to one domain - so when you start with https://monzo.com/, it would crawl all pages within monzo.com, but not follow external links, for example to the Facebook and Twitter accounts. Given a URL, it should print a simple site map, showing the links between pages.

Bonus points for tests and making it as fast as possible!

### <a name="plan">Plan</a>

##### 0. Sketch out same raw thoughts

##### 1. Identify my knowledge gaps

* I've never written anything substantial in Go
* I know almost nothing about web crawling
* I know nothing about testing in Go
* Need to figure out how to implement CI in Go
* I've never optimised a program for speed

##### 2. Tackle them

* The [Go Tour](https://tour.golang.org/welcome/1), which I should have done ages ago
* Articulate some user stories

##### 3. Design my MVP

* Is writing a web scraper a good start?
* Dream up 2/3 designs and draw some pretty diagrams (before looking at any other examples, to capture my raw ideas)
* Read up on web crawling
* Look at some other examples and compare my initial design

##### 4. Write my MVP

* The easy part 😝

##### 5. Test the shit out of it

* Realise how slow my crawler
* Identify bottlenecks

##### 6. Optimise for speed

* Tackle those bottlenecks

### Raw thoughts

So I'm trying to write a program that takes a web domain as an input (e.g. https://monzo.com/), and outputs a sitemap with the links between the pages.

I'd assume the first thing I have to do is to make a request to that webpage at the root level. I want that response to contain all of the links on that webpage. I want to store those links in some kind of data structure.

I don't want external links, so in the example above, I can reject any link that doesn't start with https://monzo.com/.

So at this point I'd presumably know the domain root and all of the links one level deep. As I want to display these in a sitemap, I need to index how deep these links are. I could give the root an index of 0, and everything I've just found an index of 1.

_I'm starting to think this could involve some recursion_

I then need to visit all of those links, and do the same, keeping track of how deep I am.

_feels like one function, taking a "depth" argument_

I'm sure I'd see massive efficiency improvements by following each of these links down to their respective bedrocks asynchronously. I'd like to explore ways of doing that. Perhaps worth designing once I've got the basic functionality sorted.

I feel like I could test drive this project pretty nicely (making a request to a domain, parsing that request, getting the links on that page, not returning the external links, ...). That would help going about this in a methodical way and ensuring I don't add anything unnecessary.

_perhaps I could just jump in and TDD the things I'm sure I'll have to do, then take a step back and think about system design more seriously. That way I'll have a better idea about the beast I'm playing with_

It seems like hitting a fully tested MVP won't be that hard (though I expect to take some time getting familiar with Go and testing in Go) Optimising will be more interesting.

It'd be interesting to go down the route of "how many requests per minute could my program handle?". Can I somehow map out how fast each bit of my program is and optimise accordingly?

Are there some unusual domain structures out there that I want to be able to handle, or are all domains structured in the same way? What are my edge cases here? I suppose I can add tests for these as I go (yay TDD!).

Questions arising from the above:

* should I start by making a request to that webpage at the root level? how else could I do this?
* what type of data structure would be most suitable to store my response in?
* how to reject external links? Can I filter them out before making the request for efficiency? Would that be significantly more efficient?
