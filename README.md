conllu.js
=========

CoNLL-U format library for JavaScript (browser & Node.js).

Installation & Usage
--------------------

### Node.js (CommonJS)

```javascript
const ConllU = require('./conllu.js');

const conlluData = `1\tThey\tthey\tPRON\tPRN\tCase=Nom|Num=Plur\t2\tnsubj\t4:nsubj\t_
2\tbuy\tbuy\tVERB\tVBP\tNum=Plur|Per=3|Tense=Pres\t0\troot\t_\t_
3\tand\tand\tCONJ\tCC\t_\t2\tcc\t_\t_
4\tsell\tsell\tVERB\tVBP\tNum=Plur|Per=3|Tense=Pres\t2\tconj\t_\t_
5\tbooks\tbook\tNOUN\tNNS\tNum=Plur\t2\tdobj\t4:dobj\t_
6\t.\t.\tPUNCT\t.\t_\t2\tpunct\t_\t_
`;

const doc = new ConllU.Document();
doc.parse(conlluData);

// Export to brat standoff format
const bratData = doc.toBrat();
console.log(bratData);

// If you want to include empty nodes in brat visualization:
const bratDataWithEmpty = doc.toBrat(null, true);
```

### Browser

Include `conllu.js` in your HTML:

```html
<script src="conllu.js"></script>
<script>
    var doc = new ConllU.Document();
    doc.parse(conlluData);
    var bratData = doc.toBrat();
</script>
```

Testing
-------

To run the automated tests using Node.js:

```bash
node test.js
```

Features & CoNLL-U v2 Support
-----------------------------

- Full support for CoNLL-U v1 and v2 specifications
- Support for multiword tokens and empty nodes (`ID` formatted as decimals like `5.1`)
- Support for spaces in `FORM` and `LEMMA` (in strict mode with TAB separators, or loose mode with 2+ spaces separating columns)
- Conversion to brat embedded format with customizable styles and sentence labels
- Validation and automatic repair of common syntax errors
