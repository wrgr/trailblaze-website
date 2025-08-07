---
layout: default
title: Media
permalink: /media/
---

<h1 class="text-primary">Media Gallery</h1>
<p>Explore videos from past College Prep Program cohorts.</p>

<div id="media-gallery" class="row row-cols-1 row-cols-md-2 row-cols-lg-3 g-4 mt-4"></div>

<script crossorigin src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
<script>
  const videos = [
    {
      title: "CPP2018 Final Movie",
      url: "http://www.youtube.com/watch?v=56bqGRyY17s",
      published: "2019-02-05",
      views: 274,
      likes: 2
    },
    {
      title: "CPP2017 Final Movie",
      url: "http://www.youtube.com/watch?v=o89eb4ad_N0",
      published: "2017-08-14",
      views: 384,
      likes: 8
    },
    {
      title: "CPP2016 Final Movie",
      url: "http://www.youtube.com/watch?v=syT7ih9DmYI",
      published: "2017-03-05",
      views: 242,
      likes: 0
    },
    {
      title: "CPP2014 Movie",
      url: "http://www.youtube.com/watch?v=nTqBhSket8Y",
      published: "2014-08-25",
      views: 305,
      likes: 1
    },
    {
      title: "CPP2013 Class Movie",
      url: "http://www.youtube.com/watch?v=Q-FVgrbrot4",
      published: "2014-02-13",
      views: 113,
      likes: 0
    }
  ];

  function VideoCard({ video }) {
    const videoId = new URL(video.url).searchParams.get("v");
    const embedUrl = `https://www.youtube.com/embed/${videoId}`;
    return React.createElement(
      "div",
      { className: "col" },
      React.createElement(
        "div",
        { className: "card h-100 shadow-sm" },
        React.createElement(
          "div",
          { className: "ratio ratio-16x9" },
          React.createElement("iframe", {
            src: embedUrl,
            title: video.title,
            allowFullScreen: true
          })
        ),
        React.createElement(
          "div",
          { className: "card-body" },
          React.createElement("h5", { className: "card-title" }, video.title),
          React.createElement(
            "p",
            { className: "card-text mb-1 text-muted small" },
            `Published: ${video.published}`
          ),
          React.createElement(
            "p",
            { className: "card-text small" },
            `Views: ${video.views} • Likes: ${video.likes}`
          )
        )
      )
    );
  }

  function App() {
    return React.createElement(
      React.Fragment,
      null,
      videos.map((video, index) =>
        React.createElement(VideoCard, { video, key: index })
      )
    );
  }

  const root = ReactDOM.createRoot(document.getElementById("media-gallery"));
  root.render(React.createElement(App));
</script>
