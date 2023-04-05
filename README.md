## before running this code
create a ".env" file under / and enter the code below while also inserting your API-Keys that you have to request via the websites linked below.

```
# API keys for the movie database

# our api key for themoviedb.org
# https://developers.themoviedb.org/3/getting-started/introduction
TMDB_API_KEY=12345

# our api key for omdbapi.com
# https://www.omdbapi.com/apikey.aspx
OMDB_API_KEY=12345
```

# Astro: Just another Movie Databases
JAMDB is a website based on the Astro Framework that allows you to search for Movies and lookup up ratings based 
on well known online critics like Rotten Tomatoes, Metacritic and the Internet Movie Database.

To access the data we are using the TMDB and OMDB API. Via TMDB we request Data for the general search and details of any movie.
Since TMDB only got their own Movie Rating we are using another API called OMDB to get ratings of more well known Services.
This works pretty well since TMDB also supplies a ID which can be used to lookup ratings on the OMDB API.

More Information regarding the APIs can be found here.  
TMDB https://developers.themoviedb.org/3/getting-started/introduction  
OMDB https://www.omdbapi.com/

## Project structure
```
/
├── public/
│   ├── images/
│   │   ├── no-image.svg.png
│   │   └── tmdb_logo.svg
│   └── favicon.svg
├── src/
│   ├── components/
│   │   ├── Card.astro
│   │   ├── Paginate.astro
│   │   └── Ratings.astro
│   ├── layouts/
│   │   └── Layout.astro
│   └── pages/
│       ├── details.astro
│       └── index.astro
└── package.json
```
## Astro
In this project I've looked into the Astro Framework and built this website based on it.
Astro is a Framework for content focused Websites and is super fast based on the approach to ship zero Javascript per default to the client.
Per design Astro is a static site Generator which uses Client-Side-Rendering although Server-Side-Rendering is supported as well.
In this Project we mainly used the templating functions as well as some styling via the Tailwind CSS integration.
Another great feature is the island architecture of astro which allows you to enable Javascript Clientside for when you really need it.

Astro provides support for many other integrations. More detailed informations can be found on the offical docs.
https://docs.astro.build/en/guides/integrations-guide/

## Main Page
On the main page I've implemented a basic search via the API to search any movie.
Per default the API looks for the Top Rated Movies if no search string is given.
Upon entering a search term into the field and pressing enter we request the same page with a URL Parameter which has our search term assigned.

In order to work with URL Parameters Server-Side-Rendering had to be enabled, as it's not possible to determine them ahead of time during the static build.
I've decided to use URL Parameters because I believe anyone should be able to get to the same page if you share it via a link. This was a decent solution since I could still work with zero Javascript and basicly generate the full site with search results based on the requested URL. There are different approaches on how to do this but this is for sure a very fast one.
https://docs.astro.build/en/reference/api-reference/#astrorequest

The URL-Parameters then will be used to make a custom API request for that given searchterm. From the API we get a response in Form of a JSON Object which will then be displayed via the Card Component. The Card component  basicly is a component that gets Data of a single movie passed onto and then creates a card with an Image, Title, Year and Link to the details Page of that movie.

Below the searchfield I've added a pagination Component fully based on the html and Astro's templating features and for styling I've used tailwind css as well as normal css that came with the astro base template.

## Details Page
On this page you can find more detailed Informations like the movie Poster, Ratings, Release-Date and more.

## Conclusion
Astro is a super fast and innovative frameworks which supports so many integrations that any web devloper should find what he's looking for.
It's very good choice for static Websites like blogs, portfolios and e-commerce websites. Espicially for blogs astro has a lot of features like pagination and more. It's easy to use and there are already plenty of templates and themes to work with.