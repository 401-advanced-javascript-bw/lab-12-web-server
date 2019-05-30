# OAuth Comparative Analysis

## GitHub

### Research Conducted By: Bonnie Wang and Jesse Van Volkinburg

### Overall Score and Comments

#### Score (Out of 10): 6

#### General Comments

- Full stack app with a link to login/sign up through GitHub.
- Generally the usability and learnability is very user friendly since it lists out all of the steps and parameters all on one page.
- Creating the client id and client secret is straightforward.

#### Pros

- Straightforward documentation, good description of (most) required parameters and methods
- Commonly used by many developers
- Extensible - permissions (scopes) are requested at time of authorization and are *added* to existing permissions allowed for that user.
- More than just a profile. Nearly full access to a user's GitHub account could be achieved.
- Granular - permission (scope) groups can be accessed en masse or individually. For example, `admin:org` is a superset of `read:org` and `write:org`.

#### Cons

- Documentation lacks some details
  - Full examples of requests and responses are not provided, though the examples and documentation are enough to get a good idea
  - Internet searches are necessary to resolve some found issues.
- User permissions requested and granted are NOT the same as the effective access received:
  - Requesting full access to the user profile does not provide access to email unless the user has allowed their email to be public.
  - Getting email addresses requires using a separate endpoint, which adds complexity to the implementation.

### Ratings and Reviews

#### Documentation

Documentation is robust and straightforward. There are no convoluted hoops to jump through, as long as basic understanding is had of the OAuth system and its usage. The documentation lacks small details such as required OAuth fields in requests, but these details are inherent to the OAuth process. Given that this is a developer-oriented site and these are docs for developers, these small oversights are not a big deal.

#### Systems Requirements

Requirements are very minimal for actually using the GitHub OAuth endpoints. A server which can perform HTTP GET and POST requests, which can parse JSON, and which can set cookies should be sufficient.

#### Ramp-Up Projections

Integrating this auth would be quite simple and take little effort. 4-5 hours should be enough to get a decent idea of how the GitHub system works.

#### Community Support and Adoption levels

GitHub has a large community of developers with 31+ million users. If the target audience is directly, or even tangentially, related to software development, then this authorization method would be fine. GitHub OAuth can be seen in several developer apps such as Swagger, Repl, Codepen, and Code Sandbox.

### Links and Resources

- [GitHub](https://github.com/)
- [GitHub OAuth Docs](https://developer.github.com/apps/building-oauth-apps/)

### Code Demos

- [live/running application](https://dashboard.heroku.com/apps/lab-12-jb)
- [Front-end code repository](https://github.com/401-advanced-javascript-bw/lab-12-web-server/tree/submission)
- [Back-end code repository](https://github.com/401-advanced-javascript-jv/12-auth-server/tree/submission)

### Operating Instructions

#### Back-end setup
- `.env` file
  * `PORT` - Port Number - Note these CANNOT be the same for both front-end and back-end
  * `MONGODB_URI` - URL to the running mongo instance/db
  * `GITHUB_CLIENT_ID` - OAuth client ID from Github
  * `GITHUB_CLIENT_SECRET` - OAuth client secret from Github
  * `SECRET` - Secret for JWT crypto
  * `API_SERVER` - URI for the `/oauth/github` endpoint - This must match the URI set below in the front-end, AND the URI set in the GitHub OAuth Apps settings.
- run `npm i` to install npm dependencies
- run `npm start` to start the back-end server

#### Front-end setup
- `.env` file
  - `PORT` - Port Number - MUST NOT match the port used for the back-end server.
* `npm start`
  * Endpoint: `/` - Entry point to the front-end app, access from a web browser

