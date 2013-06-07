# passport-stub

This is a generated Javascript version of Guilherme J. Tramontina's [@gtramontina](https://github.com/gtramontina) [passport-stub](https://github.com/gtramontina/passport-stub).

Passport.js stub for testing. | Based on Jonathon Kresner's ([@jkresner](https://github.com/jkresner)) [post](http://hackerpreneurialism.com/post/48344246498/node-js-testing-mocking-authenticated-passport-js).

Written with the idea of being simple to use.

## Usage
I've been writing my [Express](http://expressjs.com/) API tests with [Mocha](http://visionmedia.github.io/mocha/) and [Supertest](https://github.com/visionmedia/supertest), so here is an example:

```javascript
var passportStub = require('passport-stub')
  , request      = require('supertest')
  , app          = require('../app');

passportStub.install(app);
req = request(app);

describe('GET /admin', function() {

  it('responds with 401 if not logged in', function(done){
    req.get('/admin').expect(401).end();
    done();
  });

  it('responds with 200 when logged in', function(done){
    passportStub.login({username: 'john.doe'});
    req.get('/admin').expect(200).end();
    done();
  });
});
```
The user you log in with can be whatever user your app would expect to deal with. It could be a mongoose model, for example.

## Functions
 - `.install(app)`
 - `.uninstall()`
 - `.login(user)`
 - `.logout()`

## Notes
Although I didn't use, I've included a few other functions that might be useful. The code itself is pretty simple, so take a look at it.

## License
This is licensed under the feel-free-to-do-whatever-you-want-to-do license.
