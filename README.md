# week7-ifitmake-suHapi
An app which shows people involved in FACN1, where a user can see everyone involved, and add new people

[SEE IT ON HEROKU HERE](https://secret-gorge-99094.herokuapp.com/)

## Get Started
```bash
git clone https://github.com/FACN1/week7-ifitmake-suHapi.git &&
cd week7-ifitmake-suHapi &&
npm i &&
touch config.env &&
echo 'Add database URL to config.env'
```

## TO DO list

- CSS a list
- search bar functionality
  - in our query file, make a function which can take a search input and search the database for it.
  - Have a route handler for the search route (/search?)
- Add members functionality

- vote for members functionality

- Add data validation?

- Mavis' Song.


## User Stories

As a visitor to the site

> I want to see a list of all the people involved when I first visit the site

> I want to be able to search for specific or groups people involved easily (by name, location, member type etc) to get information about them

> I want to be able to add me/others to the list and see the list with me/them in it

> I want to be able to vote for my favourite member and see the number of votes members have.

As a potential applicant

> I want to find a list of people to talk to about FAC Nazareth

As a potential employer

> I want to find the 'best' candidate from FAC Nazareth to maybe hire

## Schema
**MEMBERS**

| ***Columns***  | ***Parameters  ***   |
| :------------- | :------------------  |
|       id       |  PRIMARY KEY SERIAL  |
|      name      | VARCHAR(255) NOT NULL|
|    position    | VARCHAR(100) NOT NULL|
|      location  |     VARCHAR(100)     |
|   description  |         TEXT         |
|    languages   |         TEXT         |

**Votes**

| ***Columns***  |        ***Parameters  ***           |
| :------------- |           :-------------            |
|       id       |    PRIMARY KEY SERIAL NOT NULL      |
|    member_id   | references members(id) INT NOT NULL |
|    num_votes   |              INT                    |

## HOW

- All server side rendering (i.e. using Hapi and Handlebars)

- Like in week 6, have database folder which builds and connects to a database.

- Build a HAPI server, which can use views to serve up templates, filled out with Handlebars and uses Inert to serve static files.

- Have form partials, which action gives different routes and different methods:
  - search form, with endpoint '/search'
  - add form, '/addmember'
  - vote form, '/addvote'

- Default layout will show the search form, other forms will be added with different views depending on design choices.

- Different routes will deal with different endpoints, with the handler making connections to and querying the database, will pass the information recieved from the database in the ``` reply.view('[view name here]', [data here]) ```
