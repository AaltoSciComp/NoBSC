:orphan:

Schedule
========

.. jinja:: ctx1

   Summary
   -------

   .. raw:: html

     {% for day_name, day in schedule.schedule|items%}
       <h3>{{ day_name }}</h3>

       <table class="docutils">
       <tr>
          <th></th>
          {% for room_name, room_data in schedule.meta.rooms|items %}
            <th style="vertical-align: top;">{{room_data.name}}
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
                 {% if 'id' in event %}<a href="#{{event.id}}">{{ event.title }}</a>
                 {% else %}{{ event.title }}</a>
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



   {% for day_name, day in schedule.schedule|items%}

   {{day_name}}
   ------------------------------------------------------------------------------------------

   .. raw:: html

       {% for time, sessions in day|rejectattr("time","undefined")|groupby("time") %}
       {% for event in sessions|rejectattr("id", "undefined") %}

         <section id="{{event.get("id")}}">
         <h3>{{event.title}}
	   {%if 'location' in event and 'time' in event %}
	     ({{"%02d:%02d"|format(event.time//60, event.time%60)}}, {{schedule.meta.rooms[event.location].name}})
	   {% endif %}
	   {% if 'id' in event%}<a class="headerlink" href="#{{event.id}}" title="Link to this heading"></a>{% endif %}
	 </h3>
	 {% if 'contributors' in event %}<p>Contributors: {{event.get("contributors", "")}}</p> {% endif %}

         {{event.get("abstract") |markdown |remove_newlines }}
	 </section>
       {% endfor %}
       {% endfor%}
   {% endfor %}
