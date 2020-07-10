<h1>Making a class that validates a text based on a RegEx test.</h1>

<p>I will create a class that represents a code and encapsulate the rule that the code must have a certain format.
</p>
<p>I will perform the validation in the class constructor. If the code is invalid, no object will be instantiated and the programmer will still receive an error message alerting him of the problem.
</p>

    class Code {

        constructor(text) {

            if(!this._validates(text)) throw new Error('Invalid Text');
            this._text = text;
        }

        _validates(text) {

            return /\D{3} - \D{2} - \d{2}/.test(text);
        }

        get text() {

            return this._text;
        }
    }

    let code1 = new Code('GWZ-JJ-12'); // valid
    let code2 = new Code('1X1-JJ-12'); // invalid

<p>The <code>_validates</code> method is prefixed in this way because that method should only be called by the class itself.
</p>