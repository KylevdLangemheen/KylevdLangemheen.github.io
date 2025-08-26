---
title: 'Embedding a Dynamic WebApp'
description: Streamlit and other types of webapps on my static website? Yes please!
slug: streamlit-test
date: 2025-08-26 00:00:00+0000
math: false
weight: 100
draft: false
image: streamlit.jpg
categories:
    - Visualization
    - mldl-engineering
tags:
    - Analysis
    - WebApp
---

Here is a first attempt at getting Streamlit apps embedded on this webpage. If you're unsure why this is amazing, let me explain the difference between static pages and dynamic ones. Intuitively, a static page is the same for every visitor, supports only limited interactivity, and is stored as-is on the server. It loads quickly and is so easy to host that it is completely free on many platforms. That way, to get a personal website like this one, you'd only need to pay for the DNS.

Dynamic pages are a bit different. There are server-side computations going on and served to the webclient in real-time. Typically all websites that do a bit more than just offering pages to read, such as social media platforms, e-shops, personalized user pages, and any interactivity beyond that would require dynamic content. This server has to perform more computations than just picking out the right files to send, and so usually require more set-up and come at a price.

By being able to embed dynamic content on a static page, the dynamic content can be hosted elsewhere and the interactivity still served to your website. Think for example of showing YouTube videos or ads on your webpage. The external content is loaded in dynamically when a user visits your site, while the internal content is displayed as-is. This is especially important for me because many of the projects I would want to showcase on my website require AI models or interactive data visualizations. The [PAC Winrate]({{< relref "post/pac-winrate/index.md" >}}) plot for example was directly exported as code, and the data is hardcoded in with the page. The [Nerve Growth Simulation]({{< relref "post/application-usz/index.md" >}}) is actually in 3D but I found no way to host an interactive 3D plot with this many datapoints on a static page.

Through embedding this content, I can show more (and more fun!) content in an interactive format, close to what the project is actually about. In this post I will be showcasing an example webapp I built as part of another application process. The model was already provided, the task was to do a code review on it, demo it with a webapp, and propose a future, improved, and more complete architecture. Here is the webapp in action:

<iframe
  src="https://floralpina-demo.streamlit.app?embed=true"
  style="height: 450px; width: 100%;"
></iframe>

Oops! Not all features integrate as nicely. Most notable, the callbacks for authentication breaks when running in embedded mode. Furthermore, it does not respond to the light/dark mode toggle on my website. Finally, if the page is unused for a while, Streamlit takes the container that runs the app down. This means the server essentially has to be restarted for the next visitor, which can take 5-10 minutes. It's very likely that this has happened to you just now (and then you got disappointed that you cannot login...)!

So what's the solution? Well, the easiest answer is: Don't worry about it. Running and hosting Streamlit apps is essentially free for my usecase, so it should be fine even without authentication. The light/dark mode is a bit of a pain, maybe I'll look at having a transparent background (that can dynamically be applied when running in embedded mode?). But it is by no means a dealbreaker. And it is the same with launching the app. Sure, it takes some time. But the project is there and can be easily accessed, even if it takes some waiting. For now, that is sufficient. If there's ever a need to move a project to be permanently available, I can always just spin up an instance on AWS.
