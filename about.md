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

When I was a freshman, I entered college as a double-major in piano and psychology. I had dual aspirations with this degree combination: I wanted to be able to pursue my artistic passions through music, and I wanted to acheive my dream of being a therapist. However, two roadblocks hit me almost immediately. I didn't realize the amount of practice required to major in musical performance, and I also discovered that I could have conversations of the nature I appreciated without needing to be formally trained in clinical methodology (albeit not as professionally). I initially wanted to be a therapist to be able to improve the lives of others, but I witnessed myself being able to help people simply by talking to them as a friend. On top of these observations, I also noticed that I missed doing the math and coding I conducted in high school. So, my junior year of college, I immersed myself in a variety of research experiences. The more I lived in the world of research, the more I appreciated merging the applied nature of my psychology education with the mathematical nature of statistical modeling. It might be a little bit nerdy, but I'm glad to be where I'm at. 


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
