<h1>Writting the traceback on a external file</h1>

<p>We can capture the output of a traceback as a string by calling <code>traceback.format_exc()</code>
</p>

<p>This function is useful if you want the information from an exception's traceback but also want an except statement to gracefully handle the exception.
</p>

    import traceback

    try:
        raise Exception('This is the error message.')
    except:
        with open('file_error.txt', 'w') as file:
            file.writte(traceback.format_exc())
        print('The traceback info was written to file_error.txt')