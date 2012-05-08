!SLIDE 

<p id="name">Matte Noble</p>
# REMOTELY #

!SLIDE

## API backed models and associations ##

!SLIDE

### Configuration ###

<pre class="highlighted">
<span class="class">Remotely</span>.configure do
  app <span class="symbol">:bostonrb</span> do
    url "<span class="string">http://bostonrb.org/api</span>"
  end
end
</pre>

!SLIDE

### Models ###

<pre class="highlighted">
<span class="keyword">class</span> <span class="class">Presentation</span> &lt; <span class="class">Remotely</span>::<span class="class">Model</span>
  app <span class="symbol">:bostonrb</span>
  uri "<span class="string">/presentations</span>"
<span class="keyword">end</span>
</pre>

!SLIDE

## Just like ActiveRecord::Base ##
<p class="subtitle">(mostly)</p>

!SLIDE bullets

### Endpoints ###

<table>
  <tr>
    <td>Presentation.all</td>
    <td>GET /presentations</td>
  </tr>
  <tr>
    <td>Presentation.find</td>
    <td>GET /presentations/:id</td>
  </tr>
  <tr>
    <td>Presentation.where</td>
    <td>GET /presentations/search</td>
  </tr>
  <tr>
    <td>Presentation.create</td>
    <td>POST /presentations</td>
  </tr>
  <tr>
    <td>Presentation.destroy</td>
    <td>DELETE /presentations/:id</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>presentation.save <small>(new)</small></td>
    <td>POST /presentations</td>
  </tr>
  <tr>
    <td>presentation.save <small>(retrieved)</small></td>
    <td>PUT /presentations/:id</td>
  </tr>
  <tr>
    <td>presentation.destroy</td>
    <td>DELETE /presentations/:id</td>
  </tr>
</table>

!SLIDE

### Associations ###

<pre class="highlighted">
<span class="keyword">class</span> <span class="class">Presentation</span> &lt; <span class="class">Remotely</span>::<span class="class">Model</span>
  belongs_to_remote <span class="symbol">:speaker</span>
  has_many_remote   <span class="symbol">:listeners</span>
  has_one_remote    <span class="symbol">:slidedeck</span>
<span class="keyword">end</span>
</pre>

!SLIDE

## Associations work on ActiveRecord::Base models as well. ##

!SLIDE

### Response: ###

<pre class="highlighted">
{
  "<span class="string">id</span>": <span class="number">1</span>,
  "<span class="string">name</span>": "<span class="string">Remotely</span>",
  "<span class="string">description</span>": "<span class="string">TBD</span>",
  "<span class="string">speaker_id</span>": <span class="number">2</span>
}
</pre>

### Becomes ###

<pre class="highlighted">
#&lt;<span class="class">Presentation</span> id=<span class="number">1</span> name="<span class="string">Remotely</span>" description="<span class="string">TBD</span>">
</pre>

!SLIDE

## All Together Now ##

<pre class="highlighted">
<span class="keyword">class</span> <span class="class">Presentation</span> &lt; <span class="class">Remotely</span>::<span class="class">Model</span>
  app <span class="symbol">:bostonrb</span>
  uri "<span class="string">/presentations</span>"
<span class="keyword">end</span>

presentation = <span class="class">Presentation</span>.find(<span
class="number">1</span>)
<span class="comment"># => GET /presentations/1</span>

presentation.save
<span class="comment"># => PUT /presentations/1</span>

presentation.speaker_id
<span class="comment"># => 2</span>

presentation.speaker
<span class="comment"># => Speaker.find(2)</span>
</pre>

!SLIDE

### Thanks ###

<ul class="contact">
  <li class="email"><img src="email.png"/>me@mattenoble.com</li>
  <li><img src="thetweeter.png"/>@mattenoble</li>
  <li class="github"><img src="nyan.png"/>mnoble</li>
</ul>
