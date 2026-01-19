Schedule
========

When to attend
--------------

* **For the Finnish-RSE meetup**, attend lunch on 2 Feb
  to lunch or dinner on 3 Feb.
* **For the SciComp team meetup**, attend 3 Feb until lunch on Feb 4.
* The overlapping day is events of interest to both groups.
* You are of course welcome to attend more, if you would like.

Schedule
--------

.. jinja:: ctx1

   Summary
   -------

   .. raw:: html

     {% for day_name, day in schedule.schedule|items%}
       <h3>{{ day_name }}</h3>

       <table class="docutils" style="word-wrap: break-word;">
       <tr>
          <th style="width: 10%"></th>
          {% for room_name, room_data in schedule.meta.rooms|items %}
            <th style="vertical-align: top; width: 30%">{{room_data.name}}
	    {% if 'description' in room_data %}<br><span style="font-weight: normal;">{{room_data.description}}</span>{% endif %}
            </th>
          {% endfor %}
       </tr>

       {% for time, sessions in day|rejectattr("time","undefined")|groupby("time") %}
          <tr>
          <th>{{"%02d:%02d"|format(time//60, time%60)}}</th>

          {% for room in schedule.meta.rooms %}

            <td>
            {% for event in sessions|rejectattr("location", "undefined")|selectattr("location", "eq", room) %}
               <b>
                 {% if 'id' in event %}<a
		 href="../sessions/#{{event.id}}">{{ event.shorttitle|default(event.title) }}</a>
                 {% else %}{{ event.shorttitle|default(event.title) }}
                 {% endif %}
               </b>
               {% if 'short' in event %}
                 <br>{{ event.short }}
               {% endif %}
               {%if not loop.last %}<br><br>{% endif %}
            {% endfor %}
            </td>

          {% endfor %}
          </tr>

       {% endfor %}
       </table>

     {% endfor %}
