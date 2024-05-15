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

colors for the background and other variables are stored in both _color-base.scss for the general background and _variables.scss for the other colors.