Notes for Keane:

editing the navigation pane is in _includes -> navigation

each of the 'research' posts are technically blog posts stored in collections _posts //this is not true anymore

How to put inline image: ![Charles Lindbergh lands in Paris, France](/images/the_wonderful_llms/Charles_Lindbergh_Lands_in_France.jpg)

How to put new header : ### Header

How to put hyperlink in text: [Acquired’s history of the Taiwan Semiconductor Company](https://www.acquired.fm/episodes/tsmc)

changing the 'layout' in the .md file for a page changes what it looks like...

to add a blog post, we can just add an .md file to the collections_posts

social icon links in config.yml

for each markdown (.md) file, there are certain ways to do things. for one, we can create a layout html file if we want, and set it with layout: our_layout. we can also set permalink, title, and other variables we want. To insert an inline picture, use ![Alt text](/images/research/ops.jpg "a title") (a title is optional).

the isbn number listed in the library file is specifically formatted in isbn-10. you can use isbn portal to lookup isbn number.

colors for the background and other variables are stored in both _color-base.scss for the general background and _variables.scss for the other colors. post colors are in _posts.scss.

page footer is stored in footer.html bottom-margin (default was 30px.)

page header is stored in header, I edited in a style sheet

in the html file, the style sheet thingy in CSS is signified by starting <style> and ending with </style>. 

git token needed permissions after a while of writing? I changed it in settings, but confused

So, I don't really know how it works, but the research html in _layouts is what is displaying on the research page. I believe I have it set up
correctly to display the various projects in activeresearch and previousresearch, but I could be doing it inefficiently. Each research project .md file needs
a summary to display.

the html file in layouts is the base research layout? I shifted the content to the md file so that they are disctinct from one another.

research posts are sorted by date: earliest is first

how to add a book to library: go to goodreads and export. then, move the goodreads export file to _data. Then, run the updatelibrary.py script in tools. should work.

IF you want a review with a book that has '#' in its title, I modified the updater so it handles that. just remove it in the review file name.