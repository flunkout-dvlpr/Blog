---
layout: post
title: Spotify's Web API with Spotipy!
date: 2020-01-21 21:00:00 +0300
description: 
img: SpotifyAPI_BG.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Python]
---

---

<center><h2>I enjoy python🐍 and I enjoy music🎶, why not bring it together!🤝</h2></center>
Today I'll be demonstrating the basic functionality of Spotipy, ["a lightweight Python library for the Spotify Web API. With Spotipy you get full access to all of the music data provided by the Spotify platform."](https://spotipy.readthedocs.io/en/2.7.1/)

---

<center><h2><u>Getting Started - Setup</u></h2></center>
1. Install Spotipy 
	* Simply run `pip3 install spotipy` on your python3 environment to install Spotipy

		![install Spotipy](/Blog/assets/img/SpotifyAPI_install_spotipy.gif)

2. Create a ClientID/App with Spotify 
	* Head over to [Spotify For Developers](https://developer.spotify.com/) click on ***Dashboard*** and login with your Spotify account or create a new one.
	* Click on ***Create A Client ID*** and fill out all the required fields, select ***No*** when asked if you're developing for commercial purposes
	* I already have a Client ID but I'll create another one for this example,

		![Create Client ID](/Blog/assets/img/SpotifyAPI_create_clientid.gif)  


3. Add Redirect URL
	* Part of Spotify's authorization process requires a redirect link after successful authorization, you can simply use `http://localhost/` as the redirect url
	* Under your registered app, click on ***Edit Settings*** scroll down to ***Redirect URIs*** and add `http://localhost/`, then click ***Save***

		![Create Client ID](/Blog/assets/img/SpotifyAPI_add_redirectURL.gif)  

<center><h2><u>What did we just do?</u></h2></center>
* Spotify needs a way to authenticate/authorize anyone that is trying to access their Web API, the steps above are the credentials and information Spotify will use to do so. 


---  

<center><h2><u>Authentication Flow</u></h2></center>
*  Spotipy supports two authentication methods
	* Authentication Flow :
	: This method is best for long running applications, it requires user permission once and provides a token which can be refreshed (We will be using this method)

	* Client Credentials Flow : 
	: Authenticates request directly to the Web API, this provides a higher rate limit, but only endpoints that don't access users information can be called (the reason why we wont be using this method)


* Spotipy provides a utility method, `util.prompt_for_user_token()` which authorizes the user, using the following arguments
	* username: Your Spotify account username
	* scope: The scope you want to access within Spotify's Web API, more on this below
	* client_id: The client id generated in the previous step
	* client_secret: The client secret created along with the client id 
	* redirect_uri: The redirect url we added in the previous step


* Spotify's API is broken-down into scopes, this provides confidence to the users that only information they chose to share will be shared. The scope you chose will be noted when the user is granting permission. 

* Here are the main scope categories:
	* Images
	* Spotify Connect
	* Playback
	* Users
	* Playlists
	* Library
	* Listening History
	* Follow

	[Check out the full scope details here!](https://developer.spotify.com/documentation/general/guides/scopes/)


<center><h2><u>Demo</u></h2></center>

* Using the credentials we created in the previous steps and the [`user-read-currently-playing`](https://developer.spotify.com/documentation/general/guides/scopes/#user-read-currently-playing) scope, call the utility method to authenticate
* Use the sample code below, replacing *username*, *clientId* and *clientSecret* with your own info. I'm using environment variables to store my Client ID/Secret! but you can type them in directly if you wish 
* The script will prompt Spotify's Login page, after successfully logging into your account it will redirect to another page
* Ignore the *'This site can’t be reached'* message, this happens since we used `http://localhost/` as our redirect url. Regardless the link contains the token we need to finalize the authorization process, Copy/Paste the link into the terminal. 

{% highlight python %}
import os 
import json
import spotipy 
import spotipy.util as util

username = "julio_jobs"
scope    = 'user-read-currently-playing'
clientId = os.environ['SPOTIPY_CLIENT_ID']
clientSecret = os.environ['SPOTIPY_CLIENT_SECRET']
redirectURL  = 'http://localhost/'

#Spotipy util command to authorize user
token = util.prompt_for_user_token(username, 
                                   scope, 
                                   clientId, 
                                   clientSecret, 
                                   redirectURL)

if token: 
	sp = spotipy.Spotify(auth=token)
	userDetails = sp.current_user()
	userDetails_json = json.dumps(userDetails, indent=4)
	print( "Successful LogIn!", userDetails_json)
else:
	print( "Can't get token for", username)
{% endhighlight %}

* If everything worked, the script should return a dictionary with user details associated with your account, I converted the dict to json format in order to make it a bit more readable 
* The response should look something like this 
{% highlight json %}
{
    "display_name": "julio_jobs",
    "external_urls": {
        "spotify": "https://open.spotify.com/user/julio_jobs"
    },
    "followers": {
        "href": null,
        "total": 4
    },
    "href": "https://api.spotify.com/v1/users/julio_jobs",
    "id": "julio_jobs",
    "images": [],
    "type": "user",
    "uri": "spotify:user:julio_jobs"
}

{% endhighlight %}


---
![authenticate](/Blog/assets/img/SpotifyAPI_authenticate.gif)


<center><h2><u>Let The Fun Begin! 😎</u></h2></center>


* Now that we have successfully authenticated we can start exploring Spotify's Web API and its awesome offerings,
in the following posts I will cover a project I've been working on that uses this API.
* For now checkout the some of the basic functionality in the examples below!

--- 


{% highlight python %}
userCurrentlyPlaying = sp._get("me/player/currently-playing")
userCurrentlyPlaying_json = json.dumps(userCurrentlyPlaying, indent=4)
#print(userCurrentlyPlaying)

songItem = userCurrentlyPlaying["item"]
songItem_json = json.dumps(songItem, indent=4)
#print(songItem_json)

name = songItem['name']
print(name)

albumItem = songItem['album']
albumItem_json  = json.dumps(albumItem, indent=4)
#print(albumItem_json)

albumName = albumItem['name']
print(albumName)

albumImages = albumItem['images']
imagesLinks = [image['url'] for image in albumImages]
print(imagesLinks)

artists    = songItem['artists']
artistName = [artist['name'] for artist in artists]
print(artistName)
{% endhighlight %}

![API Demo](/Blog/assets/img/SpotifyAPI_demo.gif)


<!-- <table style="width:25%">
  <tr>
    <th colspan="2"><h2><center>Library's/Packages</center></h2></th>
  </tr>
  <tr>
    <th><center>Name</center></th>
    <th><center>Link</center></th>
  </tr>
  <tr>
    <td>sys</td>
	<td>default package</td>
  </tr>
  <tr>
    <td>json</td>
	<td>default package</td>
  </tr>
  <tr>
    <td>spotipy</td>
    <td>LINK</td>
  </tr>
    <tr>
    <td>spotipy.util</td>
    <td>LINK</td>
  </tr>
</table>
 -->
