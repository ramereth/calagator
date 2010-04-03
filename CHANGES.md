Changes
=======

Key
---

  * [THEME] - Changed theme structure, see `themes/README.txt` for details.
  * [SETTING] - Changed setting structure, see `themes/README.txt` for details.
  * [SECRETS] - Changed secrets structure, see `INSTALL.md` for details.
  * [MIGRATION] - Change schema, run `rake db:migrate` to apply.
  * [DEPENDENCY] - Changed dependencies.

Changes
-------

List of Calagator stable releases and changes, with the latest at the top:

  * Next
    * Eliminated alert emails notifying admin that a form was submitted without a valid authentication token, which is almost always a spam bot.
    * Improved event form so that the end date is set to the start date if the start date is changed to be after the end date, and displayed highlight to alert user of the modification.
    * Improved event form so that the end time is offset from the start time if the start time is changed, and displayed highlighted to alert the user of the modification 

  * v0.20091223
    * [SECRETS] Added entry for setting custom Upcoming API key.
    * Added Upcoming API-based event importer, hopefully resolving long-standing problems caused by them frequently changing their invalid iCalendar output.
    * Fixed export to Google Calendar.
    * Fixed to support tags that start with numbers.
    * Fixed recent changes to not fail if showing create AND delete on same page.
    * Improved iCalendar export to mark very long events as all-day events.
    * Added "preview" feature to the event add and edit forms.
    * Added "more events" link to bottom of site's events overview.
  * v0.20091001
    * Added feature to "clone", create a new event based on an existing one, to the event's sidebar.
    * Improved recent changes, added title for each record and reorganized columns to read from left-to-right.
  * v0.20090928
    * [DEPENDENCY] + [MIGRATION] Implemented new data versioning and management system that can track and rollback deletes and more, replaces `acts_as_versioned` with `PaperTrail`.
    * Fixed how Solr determines what port to connect to, it will now always check the `config/solr.yml`.
  * v0.20090914
    * [DEPENDENCY] Upgraded to Ruby on Rails 2.3.x and updated many gems.
    * [THEME] Upgraded theme_support, which expects layouts to be in `MYTHEME/views/layouts` rather than `MYTHEME/layouts`.
    * [SETTING] Added `SECRETS.administrator_email` with email to send errors, extracted it from `config/initalizer/exception_notification_setup.rb`.
    * [MIGRATION] Added PaperTrail plugin to provide complete version tracking of all changes, including deletes.
    * Added recent changes tracking and rollback using PaperTrail.
    * Added new README.md, INSTALL.md, CONTRIBUTORS.md, and CHANGES.md files.
  * v0.2009031
    * [SETTING] Fixed timezone handling so that the application, added new `timezone` setting.
    * [THEME] Fixed layout and added an `ie.6` stylesheet.
    * Fixed duplicate checking to eliminate infinite loops and link items to their progenitor.
    * Fixed times in Upcoming imports, which violate the iCalendar standard.
    * Fixed search sort labels.
  * v0.20090503
    * Fixed error caused by removal of Time.today from RubyGems 1.3.2 and above.
    * Fixed initialization error by delaying loading of tagging extensions till tables are created.
    * Added easily customizable `config/database.yml`, see file for usage.
    * Added initial MySQL and PostgreSQL ports with many SQL fixes, however, only SQLite3 is currently recommended.
