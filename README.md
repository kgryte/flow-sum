flow-sum
========

Transform stream which returns the summation of streamed numeric data.


## Installation

``` bash
$ npm install flow-sum
```


## Examples

``` javascript
var eventStream = require( 'event-stream' ),
	sStream = require( 'flow-sum' );

// Create some data...
var data = new Array( 1000 );
for ( var i = 0; i < 1000; i++ ) {
	data[ i ] = Math.random();
}

// Create a readable stream:
var readStream = eventStream.readArray( data );

// Create a new sum stream:
var stream = sStream().stream();

// Pipe the data:
readStream.pipe( stream )
	.pipe( eventStream.map( function( d, clbk ) {
		clbk( null, d.toString() );
	}))
	.pipe( process.stdout );
```

## Tests

Unit tests use the [Mocha](http://mochajs.org/) test framework with [Chai](http://chaijs.com) assertions.

Assuming you have installed Mocha, execute the following command in the top-level application directory to run the tests:

``` bash
$ mocha
```

All new feature development should have corresponding unit tests to validate correct functionality.


## License

[MIT license](http://opensource.org/licenses/MIT). 


---
## Copyright

Copyright &copy; 2014. Athan Reines.

