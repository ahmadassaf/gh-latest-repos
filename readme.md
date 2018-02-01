# github-latest-repos

Microservice to get the latest public GitHub repos from a user with caching mechanism. 

In case you wanted to query Github for your latest repositories but do not want to waste API calls, then you can use this microservices that will query return the latest (or any other `ORDERBY` order) repos along with some metadata where the result is cached for a day.
## Example response

```js
"data": {
  "user": {
    "repositories": {
      "nodes": [
        {
          "name": "code-notes",
          "description": "Tool to summarise all code annotation like TODO or FIXME",
          "url": "https://github.com/ahmadassaf/code-notes",
          "primaryLanguage": {
            "name": "JavaScript",
            "color": "#f1e05a"
          },
          "stargazers": {
            "totalCount": 190
          },
          "forks": {
            "totalCount": 6
          }
        }
    }
  }
}
```

## How to use it?

Deploy to your hosting provider, set the below environment variables, and start it with `npm start` e.g., `GITHUB_TOKEN=XXX GITHUB_USERNAME=XXX ACCESS_ALLOW_ORIGIN=XXX npm start`

Alternatively, you can deploy it to [Now](https://zeit.co/now) [![Deploy to now](https://deploy.now.sh/static/button.svg)](https://deploy.now.sh/?repo=https://github.com/ahmadassaf/github-latest-repos&env=GITHUB_TOKEN&env=GITHUB_USERNAME&env=ACCESS_ALLOW_ORIGIN&env=MAX_REPOS):

 - Install Now and its command line
 - Execute `NODE_ENV=production -e GITHUB_TOKEN=XXXX -e GITHUB_USERNAME=ahmadassaf -e ACCESS_ALLOW_ORIGIN=ahmadassaf.com -e ORDERBY=STARGAZERS`

### Environment variables

Define the following environment variables:

- `GITHUB_TOKEN` - [Personal access token.](https://github.com/settings/tokens/new?description=gh-latest-repos)
- `GITHUB_USERNAME` - The username you like to get repos from.
- `ACCESS_ALLOW_ORIGIN` - The URL of your website or `*` if you want to allow any origin (not recommended), for the `Access-Control-Allow-Origin` header.
- `ORDERBY` - The ordering of the repos to be returned. Defaults to `CREATED_AT` (the full list of valid options are [documented here](https://developer.github.com/v4/enum/repositoryorderfield/))
- `MAX_REPOS` - The number of repos returned. Optional. Defaults to 6.

## License
MIT © [Sindre Sorhus](https://sindresorhus.com)
