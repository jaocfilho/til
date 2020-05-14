<h1>The subprocess lib</h1>

<p>The subprocess module allows you to spawn new processes, connect to their input/output/error pipes, and obtain their return codes. This module intends to replace several older modules and functions.
</p>

<p>Example usage:
</p>

    from subprocess import call
    
    call(["ls", "-l"])
