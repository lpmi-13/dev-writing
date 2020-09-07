# Dev Writing

The point of this project is to create a very basic corpus (possibly corpora) of dev writing
from various sources so we can analyze the data.

## data sources

There are a few different sources from different registers that we're going to look at.

- Github READMEs.
(https://github.com/lpmi-13/GitHubReadmeCorpus)

This was able to grab about 50 million words in a few months, and that's a very small part of the overall data that's out there, so the easiest thing to do might be to throw this up on an EC2 instance and just let it run for now. Once we're ready with some of the other data, we can see what we've got.

- Github repo source code comments

This is not a very big source of data, and a lot of the comments are likely to be "what" rather than "how" comments, but it should be simple enough to grab, so we might as well grab a bunch of it and see what we can find.

It's very possible that this will take way too long to actually collect sufficient data to be useful, since the README's are directly accessible via the Github API, whereas the source code needs a clone of the entire repo.

- Github repo PR code reviews

This is super nebulous, since we'd have no way to "filter" for code review quality (inasmuch as that metric even means anything), but perhaps we could start with the most popular or widely used projects, and assume they have a dedicated team who are able to deal with PR's and conduct code reviews.

This is the closest thing we could do to analyzing expectancy chains or reply sequences, so it is a very interesting avenue to pursue, but definitely not the low-hanging fruit at this point.

- Blog posts - dev.to
(https://docs.dev.to/api/#operation/getArticles)

The API returns all the articles without auth, so maybe building up a list of what they all are, then we can set up some rate-limited scraping on a remote VM

- Blog posts - CSS Tricks
(https://css-tricks.com/archives/)

all articles and links are available from the archive page, so should be scrapable

- Tutorials - FreeCodeCamp
(https://www.freecodecamp.org/news/tag/tutorial/)

it's easy enough to list out all the tutorials, and we don't care about any of the embedded source code anyway, so should be easy enough to scrape these.

- Documentation - ReadTheDocs
(https://docs.readthedocs.io/en/stable/api/v3.html#projects-list)

Just need an auth token to get the list of docs, and we should be able to grab everything from there.

## data collection

mostly scraping. Once the majority of what we want is compiled, will see about adding a github action to watch for changes in the RSS feed maybe? Then grab new content? Honestly, there's easily enough already up to get something useful worked up already.

The main groupings will probably be Tutorials/Docs/READMEs (I'm expecting that the docs and the readme's are going to be similar, but I suppose we can see what we see).

Other random tutorials around the internet are a bit difficult to get, since it would probably involve googling for "react tutorial" and then grabbing whatever shows up, but there's enough low-hanging fruit to not need to worry about it now.

## purpose

Similar to the [dev-talk](https://github.com:lpmi-13/dev-talk) project, the idea is to get an idea about the specific ways that devs actually write. It's a bit more important (as in higher stakes) than the way devs talk, just since there's less opportunity to negotiate meaning or repair misunderstandings in written registers. In addition, it's highly likely that the (slightly) more formal registers of dev writing are used to make judgments, either interpersonal or professional, and so I'm assuming this is an area that people are more interested in working on anyway.

Intending to focus on extracting the following main themes:

- vocabulary/grammatical structure/function for communication/discourse structure (to the extent possible)

In order to create materials to teach new developers how to "write like a developer" (something that's moreso of interest to non-native speakers), it's necessary to first figure out how developers actually write.

Unfortunately, there's no easy way to get written corpora constructed for how devs write in the workplace (Jira, Slack, Teams, code reviews, etc), so the next best thing is to compile this data from
freely available sources from roughly similar registers.

Once we've got the data, it should be possible to create material to practice reading, probably focused mostly on vocabulary. I'd like to also consider creating writing materials, but those are currently much more difficult to assess in an automated fashion.

It's not entirely outside of the realm of possibility that this data might eventually inform some sort of formal "How to write like a developer" course, but that's a long way off for the present.
