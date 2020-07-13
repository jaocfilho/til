<h1>Using boolean flag on dataclass decorator.</h1>

<p>The <code>@dataclass</code> decorator accepts a few optional Boolean flags. One of them is <code>order</code>, which results in an automatic generation of the magic methods for comparison when set to <code>True</code>
</p>

    @dataclass(order=True)
    class Person:
        ...

<p>Traditionally, you'd implement the magic method .__lt__() in your class, which stands for less than, to tell the interpreter how to compare such elements.
</p>