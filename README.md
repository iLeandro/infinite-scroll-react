#Create config folder
##Inside create server.js

module.exports = {
    APPLICATION_ID: process.env.APPLICATION_ID || 'XXXXXX',
    SECRET: process.env.SECRET || 'XXXXXXX',
    CALLBACK_URL: process.env.CALLBACK_URL || 'http://localhost:3000'
}



oUTSide config folder create serve.js
global.fetch = require('node-fetch')
const config = require('universal-config')
const Unsplash = require('unsplash-js').default
const toJson = require('unsplash-js').toJson
const express = require('express')

const unsplash = new Unsplash({
    applicationId: config.get('APPLICATION_ID'),
    secret: config.get('SECRET'),
    callBackUrl: config.get('CALLBACK_URL')
})

const app = express()

app.get('/api/photos', (req, res) => {
    unsplash.photos
        .listPhotos(req.query.start, req.query.count)
        .then(toJson)
        .then(json => res.json(json))
})

const PORT = process.env.PORT || 5000

app.listen(PORT, () => console.log(`Server started on port ${PORT}`))


# Project Title

One Paragraph of project description goes here

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

What things you need to install the software and how to install them

```
Give examples
```

### Installing

A step by step series of examples that tell you how to get a development env running

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc

