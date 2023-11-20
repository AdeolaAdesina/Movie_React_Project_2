# Movie_React_Project_2

https://www.youtube.com/watch?v=b9eMGE7QtTk&t=3531s

## Set up React Application

Using the create-react-app command. You need to have node.js installed.

```
npx create-react-app movie-app
```

Run the application with:

```
npm start
```

Now delete the src folder and create it again.

In the src folder, we will first create the index.js file.

```
import React from 'react';
import ReactDOM from 'react-dom';

import App from './app';

ReactDOM.render(<App />, document.getElementById('root'));
```


Then we create the app.js file.

```
import React from 'react';
import ReactDOM from 'react-dom';

import App from './app';

ReactDOM.render(<App />, document.getElementById('root'));
```

![Screenshot_67](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/162c2e6a-7d19-412e-8826-ce728b1fdf9c)

Now we're ready to create our application.

We're going to connect to an API to get data for what we want to build.

Now go to: https://www.omdbapi.com/apikey.aspx

Now go to your email to activate your key and copy your API Key.

Let's see how we can call this API to see all the data about movies.

In app.js use this line

```
const API_URL = 'http://www.omdbapi.com?apikey=c6a2bfd';
```

Now we can use this inside our app component to fetch the data.
We will use the useEffect hook to do that.

```
import { useEffect } from 'react';

const API_URL = 'http://www.omdbapi.com?apikey=c6a2bfd';


const App = () => {

    const searchMovies = async (title) => {
        const response = await fetch(`${API_URL}&s=${title}`);
        const data = await response.json();

        console.log(data);
    }

    useEffect(() => {
        searchMovies('Spiderman');
    }, []);
    return (
        <h1>App</h1>
    );
}

export default App;

// API Key = c6a2bfd
```

![Screenshot_68](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/f2dccf0b-bfcc-4a4c-ac9f-8d118355020a)


Now we console.log data.Search to get all the arrays.

![Screenshot_69](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/cb6411f5-75d9-4134-8c6e-11194b4cf4ac)

This shows that the API fully works. 

Now we need to be able to render this data and show it inside our application.

Now let's copy the CSS code for this application, open App.css:


```
@import url("https://fonts.googleapis.com/css?family=Roboto+Slab:100,300,400,700");
@import url("https://fonts.googleapis.com/css?family=Raleway:300,300i,400,400i,500,500i,600,600i,700,700i,800,800i,900,900i");

* {
  margin: 0;
  border: 0;
  box-sizing: border-box;
}

:root {
  --font-roboto: "Roboto Slab", serif;
  --font-raleway: "Raleway", sans-serif;
}

body {
  font-family: var(--font-roboto);
  background-color: #212426;
}

.app {
  padding: 4rem;

  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

h1 {
  font-size: 3rem;
  letter-spacing: 0.9px;
  background: linear-gradient(
    90deg,
    rgba(249, 211, 180, 1) 0%,
    rgba(249, 211, 180, 0) 100%
  );
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  width: fit-content;
}

.search {
  width: 71%;
  margin: 4rem 0 2rem;

  display: flex;
  align-items: center;
  justify-content: center;

  padding: 1.5rem 1.75rem;
  border-radius: 3rem;
  background: #1f2123;
  -webkit-box-shadow: 5px 5px 7px #1c1d1f, -5px -5px 7px #222527;
  box-shadow: 5px 5px 7px #1c1d1f, -5px -5px 7px #222527;
}

.search input {
  flex: 1;
  border: none;
  font-size: 1.5rem;
  font-family: var(--font-raleway);
  font-weight: 500;
  padding-right: 1rem;

  outline: none;
  color: #a1a1a1;
  background: #1f2123;
}

.search img {
  width: 35px;
  height: 35px;
  cursor: pointer;
}

/* .search button {
  padding: 20px 40px;
  border-radius: 0.5rem;
  margin-left: 15px;
  color: #a1a1a1;
  font-family: var(--font-raleway);
  font-weight: 900;
  letter-spacing: 0.75px;
  font-size: 1.25rem;
  cursor: pointer;
  background: #1f2123;
  -webkit-box-shadow: 5px 5px 7px #1c1d1f, -5px -5px 7px #222527;
  box-shadow: 5px 5px 7px #1c1d1f, -5px -5px 7px #222527;
} */

.empty {
  width: 100%;
  margin-top: 3rem;

  display: flex;
  justify-content: center;
  align-items: center;
}

.empty h2 {
  font-size: 1.25rem;
  color: #f9d3b4;
  font-family: var(--font-raleway);
}

.container {
  width: 100%;
  margin-top: 3rem;

  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.movie {
  width: 310px;
  height: 460px;
  margin: 1.5rem;

  position: relative;
  border-radius: 12px;
  overflow: hidden;
  border: none;

  transition: all 0.4s cubic-bezier(0.175, 0.885, 0, 1);
  box-shadow: 0px 13px 10px -7px rgba(0, 0, 0, 0.1);
}

.movie div:nth-of-type(1) {
  position: absolute;
  padding: 16px;
  width: 100%;
  opacity: 0;
  top: 0;
  color: #f9d3b4;
}

.movie:hover {
  box-shadow: 0px 30px 18px -8px rgba(0, 0, 0, 0.1);
  transform: scale(1.05, 1.05);
}

.movie div:nth-of-type(2) {
  width: 100%;
  height: 100%;
}

.movie div:nth-of-type(2) img {
  height: 100%;
  width: 100%;
}

.movie div:nth-of-type(3) {
  z-index: 2;
  background-color: #343739;
  padding: 16px 24px 24px 24px;

  position: absolute;
  bottom: 0;
  right: 0;
  left: 0;
}

.movie div:nth-of-type(3) span {
  font-family: "Raleway", sans-serif;
  text-transform: uppercase;
  font-size: 13px;
  letter-spacing: 2px;
  font-weight: 500;
  color: #f0f0f0;
}

.movie div:nth-of-type(3) h3 {
  margin-top: 5px;
  font-family: "Roboto Slab", serif;
  color: #f9d3b4;
}

.movie:hover div:nth-of-type(2) {
  height: 100%;
  opacity: 0.3;
}

.movie:hover div:nth-of-type(3) {
  background-color: transparent;
}

.movie:hover div:nth-of-type(1) {
  opacity: 1;
}

@media screen and (max-width: 600px) {
  .app {
    padding: 4rem 2rem;
  }

  .search {
    padding: 1rem 1.75rem;
    width: 100%;
  }

  .search input {
    font-size: 1rem;
  }

  .search img {
    width: 20px;
    height: 20px;
  }
}

@media screen and (max-width: 400px) {
  .app {
    padding: 4rem 1rem;
  }

  h1 {
    font-size: 2rem;
  }

  .container {
    margin-top: 2rem;
  }

  .movie {
    width: "100%";
    margin: 1rem;
  }
}
```


Also create a search.svg file:

```
<svg width="42" height="42" viewBox="0 0 42 42" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M29.8594 29.8594L39.4219 39.4219" stroke="#D88769" stroke-width="4.5" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M17.9062 33.0469C26.2682 33.0469 33.0469 26.2682 33.0469 17.9062C33.0469 9.54431 26.2682 2.76562 17.9062 2.76562C9.54431 2.76562 2.76562 9.54431 2.76562 17.9062C2.76562 26.2682 9.54431 33.0469 17.9062 33.0469Z" stroke="#D88769" stroke-width="4.5" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
```

Now import the css and search.svg in App.js

```
import './App.css';
import SearchIcon from './search.svg';
```

You'll notice the style will change:

![Screenshot_70](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/8e5f2e42-e961-4d1b-b477-005fd637b0b1)


Now we're ready to start creating the JSX of our application.

Let's start with a div and an h1 element for our heading.

```
<div className="app">
            <h1>MovieLand</h1>
        </div>
```

![Screenshot_71](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/a2b51a0c-57f7-4353-b152-60460d2aa38b)


Then another div for the search Bar.

'''
<div className='search'>
                <input 
                placeholder='Search for movies'
                />
</div>
```

![Screenshot_72](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/990b97c8-781d-41cc-8526-4fe70130c098)

![Screenshot_72](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/bddc0c04-2b74-43c2-9a89-d939c16071b3)


We're going to leave it static for now and when we implement the state, we're going edit the onchange attribute.

Below our input, we'll have a self closing image tag.

![Screenshot_74](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/58e47f85-0638-427a-b4bc-b2db9e78e193)


Now let's create a container div.

Now go to console to check the content of the container.

![Screenshot_75](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/606bc1e9-2c83-4ce3-989b-90416198bfd8)


PAste the object in App.js:

```
const movie1 = {
    "Title": "Italian Spiderman",
    "Year": "2007",
    "imdbID": "tt2705436",
    "Type": "movie",
    "Poster": "https://m.media-amazon.com/images/M/MV5BZWQxMjcwNjItZjI0ZC00ZTc4LWIwMzItM2Q0YTZhNzI3NzdlXkEyXkFqcGdeQXVyMTA0MTM5NjI2._V1_SX300.jpg"
}
```

We're going to use this as static data to render something.

![Screenshot 2023-11-20 155154](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/768847db-b2bc-406b-94d3-0b876d7bbb49)

Then we'll create another div for our image:

![Screenshot 2023-11-20 155353](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/1e161686-3714-4cda-80be-f4a18636d4fd)


Now let's add an extra check to be sure there's an image:

```
<img src={movie1.Poster !== 'N/A' ?  movie1.Poster : 'https://via.placeholder.com/400'} alt={movie1.title} />
```

![Screenshot 2023-11-20 155924](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/0c2ee3a4-d0a3-4c36-b61f-b9ecc7d15cb9)


Now we can add a span element to show the movie type and h3 to show the title:

![Screenshot 2023-11-20 160728](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/529c549a-feb8-482e-bde0-2779bfb5cb25)


Now this is just one movie and the data is static.

Now we want to fetch the data for all the movies.

The first this is to extract the code for the container div into its own custom component.

Create MovieCard.jsx:

We'll pass the movie data into MovieCard through props. And we'll use object destructuring.

MovieCard.jsx:

```
import React from "react";

const MovieCard = ({ movie1 }) => {
    return (
        <div className='movie'>
            <div>
                <p>{movie1.Year}</p>
            </div>

            <div>
                <img src={movie1.Poster !== 'N/A' ?  movie1.Poster : 'https://via.placeholder.com/400'} alt={movie1.Title} />
            </div>

            <div>
                <span>
                    {movie1.Type}
                </span>
                <h3>
                    {movie1.Title}
                </h3>
            </div>
        </div>
    )
}

export default MovieCard;
```


Inside our App.js, we can now import MovieCard.jsx

And call a custom component:

![Screenshot 2023-11-20 162957](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/444019d4-ae67-4b75-a000-87ab53bc3599)

Our application still works.

Now we want to get our movies from the API to our MovieCard component.

Now we create a new state.

App.js:

```
import { useEffect, useState } from 'react';

import MovieCard from './MovieCard';

import './App.css';
import SearchIcon from './search.svg';



const API_URL = 'http://www.omdbapi.com?apikey=c6a2bfd';

const movie1 = {
    "Title": "Italian Spiderman",
    "Year": "2007",
    "imdbID": "tt2705436",
    "Type": "movie",
    "Poster": "https://m.media-amazon.com/images/M/MV5BZWQxMjcwNjItZjI0ZC00ZTc4LWIwMzItM2Q0YTZhNzI3NzdlXkEyXkFqcGdeQXVyMTA0MTM5NjI2._V1_SX300.jpg"
}

const App = () => {
    const [movies, setMovies] = useState([]);

    const searchMovies = async (title) => {
        const response = await fetch(`${API_URL}&s=${title}`);
        const data = await response.json();

        setMovies(data.Search);
    }

    useEffect(() => {
        searchMovies('Spiderman');
    }, []);
    return (
        <div className="app">
            <h1>MovieLand</h1>

            <div className='search'>
                <input 
                placeholder='Search for movies'
                value="Superman"
                onChange={() => {}}
                />
                <img
                    src={SearchIcon}
                    alt="search"
                    onClick={() => {}}

                />
            </div>

            {
                movies?.length > 0
                ? (
                    <div className='container'>
                        <MovieCard movie1={movie1} />
                    </div>
                ) : (
                    <div className='empty'>
                        <h2>No movies found</h2>
                    </div>
                    )
            }

            
        </div>
    );
}

export default App;

```



Our app still works but we still have one static card, let's fix that.

App.js:

```
import { useEffect, useState } from 'react';

import MovieCard from './MovieCard';

import './App.css';
import SearchIcon from './search.svg';



const API_URL = 'http://www.omdbapi.com?apikey=c6a2bfd';

const movie1 = {
    "Title": "Italian Spiderman",
    "Year": "2007",
    "imdbID": "tt2705436",
    "Type": "movie",
    "Poster": "https://m.media-amazon.com/images/M/MV5BZWQxMjcwNjItZjI0ZC00ZTc4LWIwMzItM2Q0YTZhNzI3NzdlXkEyXkFqcGdeQXVyMTA0MTM5NjI2._V1_SX300.jpg"
}

const App = () => {
    const [movies, setMovies] = useState([]);

    const searchMovies = async (title) => {
        const response = await fetch(`${API_URL}&s=${title}`);
        const data = await response.json();

        setMovies(data.Search);
    }

    useEffect(() => {
        searchMovies('Spiderman');
    }, []);
    return (
        <div className="app">
            <h1>MovieLand</h1>

            <div className='search'>
                <input 
                placeholder='Search for movies'
                value="Superman"
                onChange={() => {}}
                />
                <img
                    src={SearchIcon}
                    alt="search"
                    onClick={() => {}}

                />
            </div>

            {
                movies?.length > 0
                ? (
                    <div className='container'>
                        {movies.map((movie) => (
                            <MovieCard movie={movie} /> 
                        ))}
                    </div>
                ) : (
                    <div className='empty'>
                        <h2>No movies found</h2>
                    </div>
                    )
            }

            
        </div>
    );
}

export default App;
```

Now we have to edit movie1 in MovieCard.jsx to Movie:

```
import React from "react";

const MovieCard = ({ movie }) => {
    return (
        <div className='movie'>
            <div>
                <p>{movie.Year}</p>
            </div>

            <div>
                <img src={movie.Poster !== 'N/A' ?  movie.Poster : 'https://via.placeholder.com/400'} alt={movie.Title} />
            </div>

            <div>
                <span>
                    {movie.Type}
                </span>
                <h3>
                    {movie.Title}
                </h3>
            </div>
        </div>
    )
}

export default MovieCard;
```

Now it shows only Spiderman movies

![Screenshot_76](https://github.com/AdeolaAdesina/Movie_React_Project_2/assets/29931071/0a96a8a0-0de1-412d-b445-36d745f94feb)


Now let's make the search functionality work.

And for that we'll need another state.

```
const [searchTerm, setSearchTerm] = useState('');
```

Now we'll edit our input to make it dynamic.

```
<input 
placeholder='Search for movies'
value={searchTerm}
onChange={(e) => setSearchTerm(e.target.value)}
/>
```

Then we'll also edit the img to make the click work.

```
<img
src={SearchIcon}
alt="search"
onClick={() => searchMovies(searchTerm)}

/>
```

This works fine.









