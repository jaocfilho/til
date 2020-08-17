<h1>The Calendar module</h1>

<p>This module allows you to output calendars like the Unix <code>cal</code> program, and provides additional useful functions related to the calendar.
</p>

<p>By default, these calendars have Monday as the first day of the week, and Sunday as the last. You can change it with <code>setfirstweekday</code>
</p>

    import calendar

    calendar.setfirstweekday(calendar.SUNDAY)

