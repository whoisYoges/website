+++
title = "Static website optimization tips"
date = "2023-01-24"
page_template = "page.html"
draft = false
description = ""
[extra]
gotoTop = true
shareable = true
+++
Learn some html, css tips and tricks to optimize your static website for speed and performance that anyone rarely tells you.
<!-- more -->

## Introduction
Static websites are those that are built using only HTML, CSS, and JavaScript, and do not rely on server-side scripting or databases. These types of websites are fast, secure, and easy to maintain, but they can still benefit from optimization to improve their load times and overall performance.

## Optimization Tips
for static websites include using a content delivery network (CDN), minifying HTML, CSS, and JavaScript, and compressing images. Additionally, it is important to make sure your website is mobile-friendly and uses responsive design so that it can be easily viewed on any device.

### Minimize HTTP requests
Use less number of files as possible as you can; Combine and minify CSS and JavaScript files, and use [CSS sprites](https://www.w3schools.com/css/css_image_sprites.asp) to reduce the number of images that need to be loaded.

### Optimize images
Compress images and use the appropriate image format (e.g., JPEG for photographs, PNG for graphics with transparency).  
[Shortpixel](https://shortpixel.com/online-image-compression) is one of the best online image compression tool I've discoverd so far.

### Lazy loading of images, videos and other heavy resources
Loading only what is visible to the user and loading the rest of the resources as user scrolls down the page will improve the loading time.

```
<img src="image.jpg" loading="lazy">
```

### Preload html assets
Preloading is a technique used to load resources in a webpage before they are actually needed. This allows the resources to be available immediately when they are needed, improving the overall performance of the webpage.

You can preload stylesheets, fonts, and images using the `<link>` tag with the rel attribute set to `preload` and as attribute set to `style`, `font`, or `image` respectively. For examples:

```
<link rel="preload" href="styles.css" as="style">
```

```
<link rel="preload" href="OpenSans-Regular.ttf" as="font" type="font/ttf" crossorigin>
```

```
<link rel="preload" href="image.jpg" as="image">
```

It's worth noting that preloading resources can increase the overall page load time, so it is important to be selective about which resources are preloaded and to test the performance of your webpage after preloading resources.

Another way is to use `<link rel="prefetch">` which is similar to preload but it download the resource in low priority background and it is mainly used for resources that are not immediately needed but will be needed in the future.

### Use of font-display attribute in your font family
`font-display` is a CSS property that controls how a web font is displayed while it's loading. The property can have one of the following values:

- `auto`: The default value, the browser decides how to display the font based on its own heuristics.
- `block`: The text is invisible until the font is loaded, then it is displayed.
- `swap`: The text is displayed with a fallback font until the web font is loaded, then it is swapped with the web font.
- `fallback`: The text is displayed with a fallback font until the web font is loaded, but it is not swapped with the web font.
- `optional`: The text is displayed with a fallback font, but the web font is loaded asynchronously and if the user has a good network connection it will be swapped with the web font, otherwise it will not.

In the following example, the `font-display` property is set to `swap`, so the text will be displayed with a fallback font until the `OpenSans-Regular.ttf` web font is loaded, then it will be swapped with the web font.

```
@font-face {
  font-family: 'Open Sans';
  src: url('OpenSans-Regular.ttf') format('truetype');
  font-display: swap;
}
```

### Regular update and monitoring
Always keep your code updated and monitor your website performance regularly to detect and fix issues that may arise over time.

You may use following tool/s to test the performance and speed of your website after implementing these tips to make sure they are having a positive impact on your website's speed.
- [Pingdom](https://tools.pingdom.com)
- [GTmetrix](https://gtmetrix.com)
- [DebugBear](https://www.debugbear.com/test/website-speed)