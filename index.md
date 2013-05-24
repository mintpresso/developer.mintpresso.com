---
layout: default
title: List of Documents
---

[Affogato: MINTPRESSO API for Scala](/affogato/)

### Welcome to GitHub Pages.
This automatic page generator is the easiest way to create beautiful pages for all of your projects. Author your page content here using GitHub Flavored Markdown, select a template crafted by a designer, and publish. After your page is generated, you can check out the new branch:

{% highlight bash %}
$ cd your_repo_root/repo_name
$ git fetch origin
$ git checkout gh-pages
{% endhighlight %}

{% highlight javascript linenos %}
function mintpressoInit(_){
  var user = 0
  var music = 0

  _.set({type: "user", identifier: "jin"});
  _.set({type: "music", identifier: "bugs-1000", artist: "가을방학"});
  
  $.when(
    _.get({user: "jin"}, function(json){ user = json.point }),
    _.get({music: "bugs-1000"}, function(json){ music = json.point })
  ).then(
    function(){
      // all of queries are success
      console.log("User: " + user.identifier + "\t Music: " + music.artist)
      _.get({user: "jin", did: "listen", music: "bugs-1000"}, function(json){
        if(json.status.code == 404){
          console.log(music.artist + "의 노래를 아직 듣지 못하셨군요!")
        }
      });
    },
    function(){
      // one of queries is failed
      console.log("Failed to get info.")
    }
  )
  
  var friend = 0
  var listened = 0
  $.when(
    _.get({user: "jin"}),
    _.get({user: "jin", did: "listen", music: "?"})
  ).done( function(user, list){
    /*
      Each index of user, music object contains:
        0: jsonResponse
        1: statusText
        2: jqXHR
    */
    friend = user[0].point
    listenCount = list[0].status.code == 404 ? 0 : list[0]._length
    console.log(friend.identifier + "님은 노래 " + 0 + "곡을 들었습니다.")
  })
}
{% endhighlight %}

If you're using the GitHub for Mac, simply sync your repository and you'll see the new branch.

### Designer Templates
We've crafted some handsome templates for you to use. Go ahead and continue to layouts to browse through them. You can easily go back to edit your page before publishing. After publishing your page, you can revisit the page generator and switch to another theme. Your Page content will be preserved if it remained markdown format.

### Rather Drive Stick?
If you prefer to not use the automatic generator, push a branch named `gh-pages` to your repository to create a page manually. In addition to supporting regular HTML content, GitHub Pages support Jekyll, a simple, blog aware static site generator written by our own Tom Preston-Werner. Jekyll makes it easy to create site-wide headers and footers without having to copy them across every page. It also offers intelligent blog support and other advanced templating features.

### Authors and Contributors
You can @mention a GitHub username to generate a link to their profile. The resulting `<a>` element will link to the contributor's GitHub Profile. For example: In 2007, Chris Wanstrath (@defunkt), PJ Hyett (@pjhyett), and Tom Preston-Werner (@mojombo) founded GitHub.

### Support or Contact
Having trouble with Pages? Check out the documentation at http://help.github.com/pages or contact support@github.com and we’ll help you sort it out.