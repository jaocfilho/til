<h1>Making a immutable date class property</h1>

    class Negotiation {
        constructor(date, quantity, ammount) {

            this._date = date;
            this._quantity = quantity;
            this._ammount = ammount;

            Object.freeze(this);
        }

        get date() {
            return this._date;
        }
    }

<p>If you try to instantiate an object with <code>Negotiation</code> class, you will still be able to change the date despite the <code>freeze</code> method.
For example:
</p>

    var negotiation = new Negotiation(new Date(), 1, 100);
    negotiation.date.setDate(negotiation.date.getDate() + 1);

<p>This happens because we can't freeze the methods that operates in the object. So here we have a elegant solution:
</p>

    class Negotiation {
        constructor(date, quantity, ammount) {

            this._date = new Date(data.getTime());
            this._quantity = quantity;
            this._ammount = ammount;
            Object.freeze(this);
        }

        get date() {
            return new Date(this._date.getTime());
        }
    }