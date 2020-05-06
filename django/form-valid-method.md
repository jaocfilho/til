<h1>Creating a object with the current User</h1>

<p>When you work with Django generic class-based views, it is possible to save the object using the currently logged in user when using a ModelForm.
</p>

<p>First, the ModelForm.
</p>

    # forms.py

    class BlogPostForm(forms.ModelForm):
        class Meta:
            model = models.BlogPost
            fields = ['title', 'content', 'category', 'tags']
            
<p>We do not have a user field in the ModeForm. This is on purpose as having one would show a list of all of the registered users on the site, and what we want is just the current user to be registered as the author of the post.
</p>

<p>We could fix that using a query to filter the results to just the current user, but that would be overkill, since we do not need an extra SQL query.
</p>

<p>The best way to solve this is using the form_valid() method from the CreateView.
</p>

    def form_valid(self, form):
        """If the form is valid, save the associated model."""
        self.object = form.save()
        return super().form_valid(form)

<p>Assuming the model we want to save has a ForeignKey to the User model called author, this is the code we should use.
</p>

    # views.py

    def form_valid(self, form):
        f = form.save(commit=False)
        f.author = self.request.user
        f.save()
        return super().form_valid(form)

<p>`f = form.save(commit=False)` will create the form with the input added on the website. We then add a user field with `f.author = self.request.user` and `f.save()` to save the form on the database. We finish it with the super method.
</p>

<p>If you need to save an instance of the model with the current user using the CreateView and a ModelForm, this is by far the easiest solution.
</p>