<h1>QuerySets Cheat Sheet</h1>

<p>get() returns the object matching the given lookup parameters
</p>
<p>get() raises a <code>DoesNotExist</code> exception if an object wasn't found for the given parameters.
</p>
    Place.objects.get(name='starbucks')

<p>create() is used to create and save a object in one step.
</p>
    p = Place.objects.create(name='starbucks')
