<h1>Create a Multiselect Field in a Django Model</h1>

<p>It is possible to create a field in a model that receives a list of choices as a input
</p>

    $ pip install django-multiselectfield

models.py

    from multiselectfield import MultiSelectField

    MY_CHOICES = (('item_key1', 'Item title 1.1'),
              ('item_key2', 'Item title 1.2'),
              ('item_key3', 'Item title 1.3'),
              ('item_key4', 'Item title 1.4'),
              ('item_key5', 'Item title 1.5'))
    
    class MyModel(models.Model):

    # .....

    my_field = MultiSelectField(choices=MY_CHOICES)

settings.py

    INSTALLED_APPS = (
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.sites',
        'django.contrib.admin',

        #.....................#

        'multiselectfield',
        )