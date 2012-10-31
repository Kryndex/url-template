## A JavaScript URI template implementation

This is a simple URI template implementation following the [RFC 6570 URI Template specification](http://tools.ietf.org/html/rfc6570). The implementation supports all levels defined in the specification and is extensively tested.

## Installation

    > npm install url-template

## Example

    var template = require('url-template');

    ...

    var createUrl = template('/{email}/{folder}/{id}');

    var url = createUrl({
           user: 'user@domain',
           folder: 'test',
           id: 42
        });

    console.log(url); // '/user@domain/test/42'

## A note on error handling and reporting

The RFC states that errors in the templates could optionally be handled and reported to the user. This implementation takes a slightly different approach in that it tries to do a best effort template expansion and leaves erroneous expressions in the returned URI instead of throwing errors. So for example, the incorrect expression `{unclosed` will return `{unclosed` as output. The leaves incorrect URLs to be handled by your URL library of choice.
