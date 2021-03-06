# esformatter-quotes

[esformatter](https://github.com/millermedeiros/esformatter) plugin for
single/double quotes normalization.


## Usage

install it:

```sh
npm install esformatter-quotes
```

and add to your esformatter config file:

```json
{
  "plugins": [
    "esformatter-quotes"
  ],
  "quotes": {
    "type": "single",
    "avoidEscape": false,
    "normalizeObjectKeys": false
  }
}
```


## Options

  - **type:String**
    - if code should use "single" or "double" quotes.
  - **avoidEscape:Boolean**
    - `true` if you want to avoid escaping quotes when possible.
  - **normalizeObjectKeys:Boolean**
    - `true` if you want to enforce quotes on object keys, too.

```js
// register plugin
esformatter.register(require('esformatter-quotes'));
// pass options as second argument
var output = esformatter.format(str, {
  "quotes": {
    "type": "single",
    "avoidEscape": false,
    "normalizeObjectKeys": false
  }
});
```

## Examples

Given this input program:

```js
var singleQuote = 'single';
var doubleQuote = "double";
var avoidSingle = 'single "quote"';
var avoidDouble = "double 'quote'";
var lorem = "ipsum \"dolor\" sit 'amet'";
var maecennas = 'ipsum \'dolor\' sit "amet"';
```

Will you get the following output based on the config options:


### {type: 'single'}

```js
var singleQuote = 'single';
var doubleQuote = 'double';
var avoidSingle = 'single "quote"';
var avoidDouble = 'double \'quote\'';
var lorem = 'ipsum "dolor" sit \'amet\'';
var maecennas = 'ipsum \'dolor\' sit "amet"';
```

### {type: 'single', avoidEscape: true}

```js
var singleQuote = 'single';
var doubleQuote = 'double';
var avoidSingle = 'single "quote"';
var avoidDouble = "double 'quote'";
var lorem = 'ipsum "dolor" sit \'amet\'';
var maecennas = 'ipsum \'dolor\' sit "amet"';
```

### {type: 'double'}

```js
var singleQuote = "single";
var doubleQuote = "double";
var avoidSingle = "single \"quote\"";
var avoidDouble = "double 'quote'";
var lorem = "ipsum \"dolor\" sit 'amet'";
var maecennas = "ipsum 'dolor' sit \"amet\"";
```

### {type: 'double', avoidEscape: true}

```js
var singleQuote = "single";
var doubleQuote = "double";
var avoidSingle = 'single "quote"';
var avoidDouble = "double 'quote'";
var lorem = "ipsum \"dolor\" sit 'amet'";
var maecennas = "ipsum 'dolor' sit \"amet\"";
```

## Examples for object key normalization

Given this input program:

```js
var famousQuoteBy = {
  'Princess Leia': 'I love you!',
  'Han "Shot first" Solo': 'I know!',
  Spock: 'Fascinating.',
  "Dr. Emmett 'Doc' Brown": '1.21 gigawatts???'
};

```

### {type: 'single', normalizeObjectKeys: true}
```js
var famousQuoteBy = {
  'Princess Leia': 'I love you!',
  'Han "Shot first" Solo': 'I know!',
  'Spock': 'Fascinating.',
  'Dr. Emmett \'Doc\' Brown': '1.21 gigawatts???'
};

```

### {type: 'single', avoidEscape: true, normalizeObjectKeys: true}
```js
var famousQuoteBy = {
  'Princess Leia': 'I love you!',
  'Han "Shot first" Solo': 'I know!',
  'Spock': 'Fascinating.',
  "Dr. Emmett 'Doc' Brown": '1.21 gigawatts???'
};

```

### {type: 'double', normalizeObjectKeys: true}
```js
var famousQuoteBy = {
  "Princess Leia": "I love you!",
  "Han \"Shot first\" Solo": "I know!",
  "Spock": "Fascinating.",
  "Dr. Emmett 'Doc' Brown": "1.21 gigawatts???"
};
```

### {type: 'double', avoidEscape: true, normalizeObjectKeys: true}
```js
var famousQuoteBy = {
  "Princess Leia": "I love you!",
  'Han "Shot first" Solo': "I know!",
  "Spock": "Fascinating.",
  "Dr. Emmett 'Doc' Brown": "1.21 gigawatts???"
};
```

## License

Released under the [MIT License](http://opensource.org/licenses/MIT).
