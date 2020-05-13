<h1>Using get_succes_url() method from class-based views</h1>

<p>This is a FormMixin and we use it to determine the URL to redirect to when the form is successfully validated. It return <code>success_url</code> by default
</p>

<p>We can use it to pass a dynamic URL as a argument to a <code>reverse_lazy</code> function.
</p>

<p>Example usage
</p>

    # views.py
    class ProfileUpdateView(UpdateView):
        ...
        def get_success_url(self):
            user = self.request.user
            pk = user.id
            return reverse_lazy('profile', kwargs={'pk': pk})
