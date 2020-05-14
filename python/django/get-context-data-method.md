<h1>Using get_context_data method on class-based views</h1>

<p>In Django each template is rendered with context data provided by the views.py file. By overriding <code>get_context_data()</code> we can elegantly pass this information in with our View.
</p>

<p>Example usage:
</p>

    # views.py
    class NumberView(TemplateView):
        ...
        def get_context_data(self, **kwargs):
            context = super().get_context_data(**kwargs)
	    context['number'] = random.randrange(1, 100)
	    return context
