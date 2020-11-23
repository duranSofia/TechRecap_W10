### TechRecap_Week 10

## React Lifecycle Methods

[![](https://programmingwithmosh.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-31-at-1.44.28-PM-1024x567.png)](https://programmingwithmosh.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-31-at-1.44.28-PM-1024x567.png "react lifecycle methods")

### Fetching with Axios:

```javascript
useEffect(() => {
  setAppState({ loading: true });
  const apiUrl = "https://api.github.com/users/hacktivist123/repos";
  axios.get(apiURL).then((repos) => {
    const allRepos = repos.data;
    setAppState({ loading: false, repos: allRepos });
  });
}, [setAppState]);
```

### prevProps, prevState:

= the props and state before re-render. Can be used to compare current props or state to the previous ones. Ex:

```javascript
componentDidUpdate(prevProps, nextState){
    if(prevProps.emailValue !== this.props.emailValue){
        this.setState({showError: false})
    }
}
```

<!-- ### Adding and removing favorites: -->

### Children props:

Used to display whatever you include between the opening and closing tags when invoking a component. Ex:

```javascript
const Picture = (props) {
    return (
        <div>
            <img src={props.src}/>
            {props.children}
        </div>
    )
}
```

This component contains and <img> that is receiving some props and the displaying {props.children}

Whenever this component is invoked {props.children} will also be displayed and this is just a reference to what is between the opening and closing tags of the component.

```javascript
// App.js

render(){
    return(
        <div className="container">
            <Picture key={picture.id} src={picture.src}>
            //what is placed here is passed as props.children
            </Picture>
        </div>
    )
}
```

### Props vs. State:

**Props =** data passed from parent to child
**State =** dynamic data, triggers a rerender

#### Immutable vs. Mutable data:

A **mutable object** is an object whose state can be modified after it is created.
Ex. objects, arrays, functions, classes, sets, and maps
An **immutable object** is an object whose state cannot be modified after it is created.
Ex. numbers and strings

# Relational Databases

### Database

A structure that stores organized information that it can be easily accessed, managed and updated.

### Components of a database

Schema is the tables, columns and relationships that make up a relational database.

### Relevant terms:

**SQL - Structured Query Language:** a language to extract and organize data stored in the database.

**Statement:** Atomic unit of work. Example: CREATE TABLE movies

**Query:** Request for data or information from a database.

**Database query** can be a select (retrieve data) or an action query (additional operations)

## Create a database

```
CREATE DATABASE <name of the database >;
```

```
SHOW DATABASES;
```

```
USE <dbname>;
```

```
CREATE TABLE movies (
    id INT,
    title VARCHAR(100),
    genre VARCHAR(100),
);
```

### Insert Data

```
INSERT INTO movies (id, title, genre)
    VALUES(0, ‘Matrix’, ‘Science fiction’);
```

### Select ALL

```
SELECT \* FROM movies
```

### Select specific data

```
SELECT title, genre FROM movies
WHERE genre = action
```

### Make changes in the structure of a table

```
ALTER TABLE movies
ADD year INT;
```

```
UPDATE movies SET year = 2012 WHERE id = 0;
```

```
DELETE FROM movies WHERE id = 1;
```

To empty the table data:

```
TRUNCATE TABLE <movies>
```

Delete the table:

```
DROP TABLE <movies>
```

The **LIKE** operator searches a specific pattern of one ( \ \_ ) or multiple characters ( % )

### BETWEEN

```
SELECT _ FROM movies WHERE year BETWEEN 2000 AND 2018 ;
```

### AND and OR

```
SELECT _ FROM movies WHERE year BETWEEN 2000 AND 2018 AND genre = “drama”
```

```
SELECT \* FROM movies WHERE genre = “crime” OR genre = “suspense”
```

### Sorting data

```
SELECT * FROM movies ORDER BY title ASC (ascending)
```

```
SELECT * FROM movies ORDER BY title DESC (descending)
```

### LIMIT

```
SELECT _ FROM movies ORDER BY year DESC LIMIT 4;
COUNT
```

### GROUP BY

```
SELECT campus, COUNT (*) as number_of_movies
FROM movies
GROUP BY genre;
```
