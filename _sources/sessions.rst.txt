List of sessions
================

This list currently only has the pre-planned "keynote" sessions
invited by the organizers for the SciComp meetup (the second half).


Discussion: The current hardest legal questions in research data and computing
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We often hear clear-cut instructions about legal matters in research
(copyright, data, ethics, intellectual property, and especially AI
these days).  Yet humans are behind the scenes, reading and
interpreting the legislation, court cases and legal literature and
producing these guidelines, and it isn't always so clear-cut.  This is
a discussion with Maria Rehbinder, Legal Counsel, Aalto University,
where we'll peek "behind the cutains" at some of the open questions
going around right now, especially related to AI.  This will start a
two-way discussion about all of these legal matters.

Maria Rehbinder is a Senior Legal Counsel at Aalto University.  Her
traditional standard projects included copyright, trademarks, and
design rights, but more recently has been involved in the initial
implementation work of legislation such as the GDPR, AI Act, and
Digital Services Act.  Maria serves as a member in the Copyright
Commission and the Copyright Council of the Ministry of Education and
Culture and as a member in the Rights ManagementCommittee of Open
Research and Science 2014-2017 initiative of the ministry.


The role of Research Software Engineers and SciComp teams in universities
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

What is the role of Research Software Engineers, and teams of them, in
universities in the future?  Heikki Manilla was president of the
Research Council of Finland (then the Academy of Finland) from
2012-2022 and now the director of the "House of AI", an Aalto project
helping to connect various disciplines in the use of AI and scientific
computing.  Heikki will present the funders' side of things and give
some vision for how research engineer and scientific computing teams
can be made sustainable in the future.


Cool things and problems
~~~~~~~~~~~~~~~~~~~~~~~~

Our icebreaker of the workshop, and starting point for sharing ideas.
Everyone (hopefully grouped into teams from their organization) can
present one slide of three cool things they have done lately, and one
slide of three problems they are facing lately.  We will quickly go
through these and use the talk as a starting point for discussion -
maybe a few unconference talks can be requested from it.

The session will be built from a shared editable slide deck.
Attendees will get contribution instructions (+ more details) closer
to the event.


Panel discussion: New HPC user perspective
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Panel discussions are usually full of the most senior people the
organizers can find.  In this discussion, we'll hear from junior
researchers, just started in their HPC/SciComp journey, about how
usable they see computing systems and the onboarding process.




..
   Below is a list of some of the known sessions we'll have.
   
   .. jinja:: ctx1
   
      .. raw:: html
   
          {% for day, sessions in schedule.schedule|items %}
          {% for event in sessions|rejectattr("id", "undefined") %}
   
            <section id="{{event.get("id")}}">
            <h3>{{event.title}}
   	   {%if 'location' in event and 'time' in event %}
   	     <!--({{"%02d:%02d"|format(event.time//60, event.time%60)}}, {{schedule.meta.rooms[event.location].name}})-->
   	   {% endif %}
   	   {% if 'id' in event%}<a class="headerlink" href="#{{event.id}}" title="Link to this heading"></a>{% endif %}
   	 </h3>
   	 {% if 'contributors' in event %}<p>Contributors: {{event.get("contributors", "")}}</p> {% endif %}
   
            {{event.get("abstract") |markdown |remove_newlines }}
   	 </section>
          {% endfor%}
          {% endfor%}
