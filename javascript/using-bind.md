<h1>Using bind syntax and avoid going through the DOM many times</h1>

<p>Suppose that you have the following controller.
</p>

    class NegotiationController {

        add(event) {

            event.preventDefault();

            let inputDate = document.querySelector('#date');
            let inputQuantity = document.querySelector('#quantity');
            let inputAmmount = document.querySelector('#ammount');

        }
    }

<p>This code works, but as you can see we repeated the code a lot, it was a laborious syntax to be typed
</p>
<p>To solve that in a elegant way we can create a new variable called <code>$</code>, and put <code>document.querySelector</code> inside it.
</p>

    class NegotiationController {
        
        add(event) {

            event.preventDefault();

            let $ = document.querySelector;
            let inputDate = $('#date');
            let inputQuantity = $('#quantity');
            let inputAmmount = $('#ammount');

        }
    }

<p>This way, it was less work to write the code. But if we run it as is, we will see an error message in the browser.
</p>
<p>The <code>querySelector</code> is a function that belongs to the document object - we will call that function a method. Internally, the <code>querySelector</code> has a call to <code>this</code>, which is the context from which the method is called.
</p>
<p>To solve that we need to maintain te association between <code>document</code> and <code>querySelector</code>, for that we can use <code>bind()</code>.
</p>

    class NegotiationController {
        
        add(event) {

            event.preventDefault();

            let $ = document.querySelector.bind(document);
            let inputDate = $('#date');
            let inputQuantity = $('#quantity');
            let inputAmmount = $('#ammount');

        }
    }

<p>Now it works, but there is one last thing to do. Out code is running through the DOM many times and this is a bad practice, since it compromises the performance of the page.
</p>

    class NegotiationController {

        constructor() {

            let $ = document.querySelector.bind(document);

            this.inputDate = $('#date');
            this.inputQuantity = $('#quantity');
            this.inputAmmount = $('#ammount');
        }

        add(event) {

            event.preventDefault();

        }
    }