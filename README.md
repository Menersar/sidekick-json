# sidekick-json

This library is intended to parse and stringify non-standards-compliant JSON:

 - Parser and stringifier support `Infinity`, `-Infinity`, and `NaN`
 - Parser supports comments with `// ...` and `/* ... */`
 - Parser supports trailing commas
 - Parser supports extra ignored data after the end of the JSON value

Install from npm:

```bash
npm install https://github.com/Menersar/sidekick-json
```

Then pick your favorite way to import it:

```js
import {parse, stringify} from 'sidekick-json';
import * as ExtendedJSON from 'sidekick-json';
const ExtendedJSON = require('sidekick-json');
```

Note that there is no `default` export, so `import ExtendedJSON from 'sidekick-json';` might not work.

parse() parses a JSON string. It will first try to use JSON.parse, and falls back to our custom JSON parser if that fails. JSON.parse's reviver argument is not supported.

_parse() is also exported. It skips trying to use JSON.parse and always uses our custom JSON parser.

stringify() converts a JSON object to a string. Does not support JSON.stringify's replacer or space arguments. The resulting string is always fully minimized.

Our custom JSON parser and stringifier are not particularly optimized, but they are probably *fast enough*. The native JSON parser and stringifier are substantially faster than our custom ones.
