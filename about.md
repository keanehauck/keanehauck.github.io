---
layout: about
permalink: /about/
title: A little bit about me.
tags: about
headshot: /images/headshot.jpg
---

### Where I'm from

I was born and raised in the city of Cincinnati, Ohio — right next to train tracks and a creek where I could catch [crawdads](https://www.nationalgeographic.com/animals/invertebrates/facts/crawdads) (_definitely_ not "crayfish").

I moved to Kansas when I was around 8 years old - and completed my pre-college education at the Andover school district. The bulk of my passions in high school concerned computers and coding; however, I also appreciated the soft sciences. From there, I made my way to the University of Oklahoma, where I currently am pursuing a Bachelor's of Science in psychology and taking computer science and music courses on the side.

### What I do now

Currently, I conduct research in a variety of subdisciplines; however, my area of specialty lies in quantitative methodology. I also spend my time building keyboards and writing music (when I'm not playing video games). [Take a look at my research!]({{ site.baseurl }}/research)

### Where I'm at now

Today, I live in Norman, OK. When I'm not working or attending class, you can find me walking around Main street or nearly entering cardiac arrest on a bicycle. I also love to frequent some of the coffee shops around the city, especially Gray Owl and Yellow Dog.

### Why quantitative methodology?

My answer for "why" spans three levels: the micro, the macro, and the philosophical. On a micro level, I really enjoy statistics. I initially started college as a psychology major because I wanted to be a therapist and enjoyed the study of human behavior. However, the longer I was in school, the more I realized that I missed mathematics and the harder sciences, so I returned to coding, computer science, and research. I soon stumbled across quantitative methodology as a perfect blend of all my passions. On a macro level, I really want to be a professor. I love teaching—I currently tutor a student in statistics and provide consent trainings to incoming students. Additionally, the environment of academia seems like a place where I could spend the rest of my life. On a philosophical level, I really want to play a part in facilitating a more holistic union of the psych field with the stats field. Does the term replication crisis ring a bell? I believe that we, as psychologists, need to reassess how we interact with the field of quantitative methodology, both in our pedagogy and in our practice.

### Get in touch!

The easiest way to contact me is through email: [keane@ou.edu](mailto:keane@ou.edu). Please allow up to 2 business days for a response due to the unfortunate user error of chronically failing to notice new emails in my inbox.

<div id="stats" class="hidden">

<h3 id="dashboard"><code>#dashboard</code></h3>

<h2>Just finished.</h2>

<p>Curious what I'm reading? Here's my most recent reads, updating daily. And my <a href="https://www.goodreads.com/user/show/88184044-jonathon-belotti)" target="_blank" rel="noopener noreferrer">Goodreads profile</a> has more history.</p>

<div id="recent-finished-books"></div>

<h2>Top tracks.</h2>

<p>Curious what I'm currently listening to? Here's my top tracks on Spotify, updating daily.</p>

<ol id="top-spotify-tracks"></ol>

</div>

<script>
/**
 * @param {String} HTML representing a single element
 * @return {Element}
 */
function htmlToElement(html) {
    var template = document.createElement('template');
    /* Never return a text node of whitespace as the result */
    html = html.trim();
    template.innerHTML = html;
    return template.content.firstChild;
}

function populateDashboardHTML(data) {
    const topSpotifyTracksList = document.querySelector('#top-spotify-tracks');
    data.spotify.forEach(track => {
        topSpotifyTracksList.appendChild(htmlToElement(`
            <li>
                <a target="_blank" rel="noopener noreferrer" href="${track.link}"><strong>${track.name}</strong></a> 
                <p>${track.artist}</p>
            </li>
        `));
    });

    const recentFinishedBooks = document.querySelector('#recent-finished-books');
    data.goodreads.slice(0, 3).forEach(book => {
        recentFinishedBooks.appendChild(htmlToElement(`
            <a target="_blank" rel="noopener noreferrer" class="book-item" target="_blank" rel="noopener noreferrer" href="${book.link}">
            <div class="cover-container">
                <img class="grow-me" src="${book.cover_image_link}">
            </div>
            <div class="book-info">
                <h4>${book.title}</h4>
                <p>${book.authors[0]}</p>
            </div>
            </a>
        `));
    });
}

fetch('https://thundergolfer-cgflgpx.modal.run')
  .then((response) => {
    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    return response.json();
  })
  .then((data) => {
    populateDashboardHTML(data);
    /* Reveal the now populated stats section. */
    document.getElementById("stats").classList.remove("hidden");
  });

</script>

<style>
#stats {
  background-color: #f7f7f9;
  border-radius: 1rem; 
  padding: 1.5em;
  margin-top: 2.5em;
}

#dashboard {
  margin: 0rem;
}

#dashboard code {
  background-color: #f7f7f9;
}

#recent-finished-books {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    justify-content: center;
}

#recent-finished-books a {
    color: #111;
}

.book-item {
    margin-left: 0.4em;
    margin-right: 0.4em;
}

.book-item div {
    width: 200px;
}

.book-info h4 {
    color: #222;
}

.book-info p {
    color: #555;
}

.grow-me {
  border-radius: 4px;
  transition: all .2s ease-in-out;
}

.grow-me:hover {
  transform: scale(1.02);
}

#top-spotify-tracks {
    padding-left: 1em;
}

#top-spotify-tracks li {
    color: #888;
    border-bottom: 1px solid #ededed;
    margin-top: 1rem;
}

#top-spotify-tracks a {
    color: #111;
}

#top-spotify-tracks a:hover {
    color: #1DB954; /* Spotify green */
}

#top-spotify-tracks p {
    color: #555;
}

.hidden {
    display: none;
}

@media screen and (max-width: 900px) {
  #recent-finished-books {
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .book-item div {
    width: 400px;
  }

  .book-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .cover-container, .book-info {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  #top-spotify-tracks {
    padding-left: 1.2em;
  }
}
</style>
