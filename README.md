# Web Crawler 🕷

I'm gonna write me a web crawler in Go!

_def: A Web crawler, sometimes called a spider, is an Internet bot that systematically browses the World Wide Web, typically for the purpose of Web indexing (web spidering). Web search engines and some other sites use Web crawling or spidering software to update their web content or indices of others sites' web content._

### Brief

To write a simple web crawler, limited to one domain - so when you start with https://website.com/, it would crawl all pages within website.com, but not follow external links, for example to the Facebook and Twitter accounts. Given a URL, it should print a simple site map, showing the links between pages.

Bonus points for tests and making it as fast as possible!

### Plan

##### 1. Become aware of my knowledge gaps

* I've never written anything substantial in Go
* I know almost nothing about web crawling
* I know nothing about testing in Go
* I've never optimised a program for speed

##### 2. Do these preliminary things to do

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
