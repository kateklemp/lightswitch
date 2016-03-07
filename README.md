# LightSwitch

A lightweight HTML5 single-page website using jQuery templating to switch content

### Prerequisities

* A server for local development (I recommend [node.js http-server](https://www.npmjs.com/package/http-server) because it's fast and easy)
* A text editor or your preferred IDE
* A browser that renders Javascript

### Installing

Clone the repo locally, navigate to the repo folder, fire up your web server, view in the browser, edit in your IDE

The initial version has no styling or templating; this is meant to be as bare a repo as possible while still maintaining simple HTML5 standards, semantic elements, and a simple div to switch content out on-click of nav elements.  I have included several pages for demonstration.

### How it works

All the actual functional code is inside `index.html`

The script at the bottom of the index page does three things:
1) sets the initial template to `pages/main.html`
2) sets up the header tag to load `pages/main.html` if clicked anywhere
3) loops through the nav divs to get their ids, then loads the template with the matching name inside the `pages` directory

```
<script>
  $('#content-container').loadTemplate('pages/main.html');
  $('header').click(function(){
    $('#content-container').loadTemplate('pages/main.html');
  })
  $('nav').children().each(function() {
    $(this).click(function() {
      $('#content-container').loadTemplate('pages/' + $(this).attr('id') + '.html');
    });
  });
</script>
```

To add a page, create a new div inside the `nav` tags with `id="pagename"`, then create a template at `pages/pagename.html`.

```
<nav>
  <div id="main">Home</div>
  <div id="about">About Us</div>
  <div id="portfolio">Portfolio</div>
  <div id="contact">Contact</div>
</nav>
```

To delete a page, delete both the `div` in `index.html`, and the template inside the `pages` directory.

To change a page, change the value of the `id` in its `div`, and change the name of the template inside the `pages` directory.

As long as the `id` and the template name inside the `pages` directory are the same, the templating will work.

Content is loaded into the article tag inside the div with `id="content-container"`

```
<article>
  <div id="content-container"></div>
</article>
```

## Running the tests

*Coming soonish*

## Deployment

FTP or your choice of deploy process - this is meant to be a vanilla install with all working parts in tact, without a strong opinion about deployment or environment setup

## Built With

* [Atom Editor](https://atom.io/)
* [jQuery.loadTemplate](https://github.com/codepb/jquery-template)
* [html5Doctor HTML5 boilerplate](http://html5doctor.com/html-5-boilerplates/)
* [PureCSS](http://purecss.io/)
* [jQuery v2.2.1 CDN](https://code.jquery.com/)


## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/kateklemp/lightswitch/tags).

## Authors

* **Kate Klemp** - *Initial work* - [kateklemp](https://github.com/kateklemp)

See also the list of [contributors](https://github.com/kateklemp/lightswitch/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* [OpenGovernment's Contributing Documentation](https://github.com/opengovernment/opengovernment/blob/master/CONTRIBUTING.md)
* [Atom Editor's Contributing Documentation](https://github.com/atom/atom/blob/master/CONTRIBUTING.md)
