# Introduction to our Project

Don't worry - you are not expecting to come up with a project from the ground up. Instead we'll be working on a small sample project that you can find in [this](https://github.com/sQu4rks/CICD-Hands_On-Demo) repository. 

Our project is a small guestbook API that stores the name, timestamp of creation and the guestbook entry into a [redis](https://redis.io/) instance. We interface with the flask-based web service via a very simple REST interface. The two operations that are supported are:

* `POST /api/posts` to create a new entry
* `GET /api/posts` to retrieve all entries

When sending a `POST` request to the endpoint it takes the following JSON payload:

```json
{
   "text": "<Your guestbook entry>",
   "author": "<Name of the author>"
}
```
Upon success, the endpoint will return a JSON payload with the following structure:

```json
{
   "text": "<Your guestbook entry>",
   "author": "<Name of the author>",
   "id": <id of your entry>,
   "timestamp": "<Timestamp in unix time>"

}
```

When sending a `GET` request to the endpoint you will get a paginated result. By default a page size of 10^10 is retrieved. You can influence the start of your page as well as the length using the following two query parameters:

* `start` will change the first entry in the list that is retrieved
* `length` changes the page size

As an example, a query to `GET /api/posts?start=5&length=10` would retrieve 10 items starting at the 5th newest entry.

A succesfull request returns a JSON payload like this:

```json
{
   "start": <start of your list - default: 0>,
   "length": <length of your page requested - default: 10^10>,
   "size": <actual number of items>,
   "items": <list of entries>
```

each entry is represented by a JSON object that has the following properties:

```json
{
   "text": "<Your guestbook entry>",
   "author": "<Name of the author>",
   "id": <id of your entry>,
   "timestamp": "<Timestamp in unix time>"

}
```

The repository also includes various support scripts such as a local setup script as well as a `docker-compose.yml` file. 

<div align="right">
   
   [Prev](01_intro-to-cicd.md) - [Next](03_run-project.md)
</div>
