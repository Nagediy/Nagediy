# Nagediy

Nagediy - Neither CMS nor JAMStack.

Stop wasting your valuabel time with .yaml config files and command line configurations. We are living in 2022, the time of using consoles should be over. Also working with a GUI is way more fun. 

* [What do you get?](#what-do-you-get)
* [Why this repot?](#why-this-repo)
* [Installation](#installation)
* [Server Tweaks](#server-tweaks)
* [Notes](#notes)
* [Support](#support)  


## What do you get?
A minimalist pug-boilerplate to create static sites.

A SSG with minimal configs. Use Tools with GUI for easy handling. No more spending too much time with config files or command line scripts. Welcome to 2022!

### Features

- Atomic CSS/JS (also minified)
- automatic CSS/JS/Image optimization (with the right tools)
- static .html files
- PUG as template engine to reuse HTML
- Just files and folders (really!)

### Tools

- [Prepros](https://prepros.io/)
- [Codekit](https://codekitapp.com/) (able to do the same, but not testet)

### Addons

- RSS
- Sitemap
- GDPR Cookie

## Why this repo?
An appraoch to provide an easy entry point to work with HTML, CSS, JS by the enduser itself.

* re-use pug (html) snippets, e.g. head meat, navigation or footer.
* keep files size low.
* update navigation pug for instance and other sites automatically update (Prepros Pug feature)

Just SFTP Access to automatically upload the page or deploy via git

## Installation:
1. Unzip the files.
1. Download [Prepros](https://prepros.io/)
1. Add directory in Prepros
2. Start coding

### Packages for Prepros

See error messages when compiling .md files with markdown filter:

Minimum Requirement: 

- jstransformer-markdown-it
- jstransformer-coffee-script (optional)

## Server Tweaks

### Nginx

#### Headers

##### Server
```
add_header Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-hashes' 'sha256-uq+4nUqZONgARzmy2kR1w9EC+Qeig/Syd091LyT8vOk=' https://api.pirsch.io https://unpkg.com; form-action 'self' https://submit-form.com https://submitted.formspark.io; style-src 'self' https://fonts.googleapis.com; object-src 'self'; base-uri 'self'; connect-src 'self' https://api.pirsch.io https://api.botpoison.com; font-src 'self' https://fonts.gstatic.com; frame-src 'self'; img-src data: 'self' https://github.kreativ-anders.dev https://source.unsplash.com https://images.unsplash.com; manifest-src 'self'; media-src 'self'; worker-src 'none';";

add_header X-Content-Type-Options "nosniff" always;
add_header X-Frame-Options SAMEORIGIN always;
add_header X-XSS-Protection "1; mode=block" always;
```

##### Root
```
location ~* \.(?:css|js)$ {
  expires 1w;
  add_header Cache-Control "public";
}

location ~* \.(?:gif|png)$ {
  expires 1y;
  add_header Cache-Control "public";
}

location  /404.html {
  internal;
}

error_page 404 /404.html;
```

## Notes:

> No use of extend, since this will raise an error reagrding blocks. But Meta information should be on the top for usability. So includes rather extends. The philosophy deu to tempkates stays true.

Prepros offers a simple user interface to manage the compilation from .pug to .html.
To create a new page, just add a folder, e.g. "faq", and add index.pug file. Afterwards, you cann access the page (https://domain.tld/team). Most webservers can handle this request automacially and forward to the index.html file inside.

> Do not use Typora Export, even footnotes are working well. Images are kind of troublemakers since thos eare referenced with direct path wwich leads to crash

> Check Notification Setting within Prepros. Especially for websites with a lot of automatic processing it might yield a lot of notification that slow down your process.

> Be craeful when using purgecss: purge base is based on final html outcome issues with dynamic changes, e.g. disabled button with JavaScript or set aria-busy/invalid Attribute (therefore CSD needs to be manually adjusted afterwards)

> Best for small websites. Blogs are possible, but require a powerful machine to process fast.

> The folder setup leads to URLS with a traling slash at the end. Please be aware of that fact, since it may be important when upgrading to another solution, e.g. CMS.

> Use small hierarchies and avoid loopholes to increase processing performance.


## Disclaimer
The source code is provided "as is" with no guarantee. Use it at your own risk and always test it yourself before using it in a production environment. If you find any issues, please create a new issue.

## Support

In case this boilerplate saved you some time and energy consider supporting kreativ-anders by donating via [PayPal](https://paypal.me/kreativanders) or becoming a **GitHub Sponsor**.

## Examples


- See https://github.com/kreativ-anders/website (Private, new example comes soon)
- See https://github.com/Manuel-Steinberg/Lesestoff (Private book collection)
