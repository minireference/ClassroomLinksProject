
Classroom Links: Software Requirement Specification
===================================================


Web application modelled on generic social site with the following URL structure:

  - `/classrooms/` = list of classrooms
  - `/classrooms/813981309/` = classroom details page for classroom id=813981309
  - `/links/` = map dashboard showing current classroom links and faded-version of past links on a world map
  - `/links/8284-32oi323-232332-23112/`
    A basic info page that shows a link to a google hangout, a viber ID/phonenumber, a skype ID, or other info needed to esablish link between two classrooms.
    (users can share this link by email, sms, or other msging means. If you know this difficult-to-guess URL, you have access to the contact info of all parties in live link so can join)




MMVP Scenarios
-------------

  - As a teacher, I can sign up using gmail, yahoo, twitter, or faceboook id.
  - As a teacher, I can classroom profile
    - wizard will ask me to create a school profile first if school doesn't exist yet
  - As a teacher I can start a live link session.



MVP Scenarios
-------------

  - As a teacher I can schedule a classroom link
  - As a teacher I can read and write comments on the live link page
  - As a student I can read comments on the live link page



Data model
----------

Setup project with basic stuff from django cookicutter:
  - User account
  - UserProfile?
  - social SingUp



Models for MMVP:


    Teacher(User)
        username
        email
        first_name
        last_name


    School
        mailing_address
        map_coordinates
        timezone


    Classroom
        id
        name
        school --> 'School'
        teacher --> 'Teacher'
        student_ages


    ClassroomLink
        id = UUID
        permalink = e.g. /links/8284-32oi323-232332-23112/
        short_url = e.g. bit.ly/a84u238
        extra_instructions
        classroom_left --> 'Classroom'
        classroom_right --> 'Classroom'

        comments --> list of 'LiveComment' (can be of kind = 'left' or 'right')
        left_ips  # ['193.32.21.15', '32.56.77.8'] ip based access control for comments
        right_ips

        created__datetime
        modified_datetime
        scheduled_datetime
        scheduled_duration
        started_datetime
        ended_datetime






