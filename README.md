We're going to build ourselves a Sinatra sandbox that we can use to better understand the flow of data through a web application.
<h2>Learning Goal</h2>
By the end of this challenge, you should be able to answer questions like:
<ol>
	<li>Where does the browser "enter" my code?</li>
	<li>Where does the server "return back" to the browser?</li>
	<li>When do views get rendered?</li>
</ol>
<strong>Don't rush through this challenge!</strong>

As always, you can <a href="http://ge.tt/3PfpXR22/v/0">get the Sinatra skeleton here</a>.
<h2>Objectives</h2>
<h3><code>puts</code> debugging</h3>
<code>puts</code> debugging is something every developer does regularly. When confronted with total confusion about how parts of the code are interacting with each other, a developer will place <code>puts</code> statements everywhere to see what methods are called when and what's happening inside each method.

This isn't cheating, this isn't giving up, this isn't something beginners do. In the Real World, nobody cares if you debug a problem using <code>puts</code>, they only care that you debugged the problem.

We're going to use <code>puts</code> debugging on this Sinatra app.
<h3>Build a Dummy App</h3>
In your controller code, add the following routes:
<div class="highlight">
<pre>get <span class="s1">'/'</span> <span class="k">do</span>
  puts <span class="s2">"[LOG] Getting /"</span>
  puts <span class="s2">"[LOG] Params: #{params.inspect}"</span>
  erb :index
end

get <span class="s1">'/cool_url'</span> <span class="k">do</span>
  puts <span class="s2">"[LOG] Getting /cool_url"</span>
  puts <span class="s2">"[LOG] Params: #{params.inspect}"</span>
  erb :get_cool_url
end

post <span class="s1">'/cool_url'</span> <span class="k">do</span>
  puts <span class="s2">"[LOG] Posting to /cool_url"</span>
  puts <span class="s2">"[LOG] Params: #{params.inspect}"</span>
  erb :post_cool_url
end
</pre>
</div>
Create <code>index</code>, <code>get_cool_url</code>, and <code>post_cool_url</code> views. The <code>get_cool_url</code> and <code>post_cool_url</code> views can contain whatever you want to make it easier for you to explore how Sinatra, forms, and the HTTP request cycle works.

Create a simple page with two forms in the <code>index</code> view. It should have one text field; you can call it whatever you want. It should also have a submit button.

The first form should submit a <code>GET</code> request to <code>/cool_url</code>. The second form should submit a <code>POST</code> request to<code>/cool_url</code>.
<h3>Add More Form Elements</h3>
Explore what happens when you add other kinds of form elements to your form. Add fields of the following types:
<ul>
	<li><a href="http://www.echoecho.com/htmlforms08.htm">Textarea</a></li>
	<li><a href="http://www.echoecho.com/htmlforms10.htm">Radio buttons</a></li>
	<li><a href="http://www.echoecho.com/htmlforms09.htm">Checkbox buttons</a></li>
	<li><a href="http://www.echoecho.com/htmlforms11.htm">Select box</a></li>
</ul>
Observe how they interact with <code>params</code> on the server side. Play around and add more logging if you want.
<h3>Add New Form Element Names</h3>
Add the the following inputs to one or all of your forms:
<div class="highlight">
<pre>&lt;input <span class="nb">type</span><span class="o">=</span><span class="s2">"text"</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"post[title]"</span>&gt;
&lt;input <span class="nb">type</span><span class="o">=</span><span class="s2">"text"</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"post[price]"</span>&gt;
&lt;textarea <span class="nv">name</span><span class="o">=</span><span class="s2">"post[description]"</span>&gt;&lt;/textarea&gt;
</pre>
</div>
How does this impact the <code>params</code> hash on the server side?
<h3>Upload a Gist</h3>
Upload a gist that contains a link to your application's repository and a list of 5-10 questions you have about how Sinatra applications, the web, web applications in general, HTML forms, etc. work.
<h3>Your Own Experiment</h3>
Come up with your own experiment to partially answer at least 2 of the questions you have from above. What debugging statements (<code>puts</code> or otherwise) can you add to help you answer your question?

If you can't answer the entirety of your question, can you answer part of it? For example, "I don't know where exactly something happens, but I know it happens after we call <code>erb</code>."

Make your question simple and small enough that you can see how to answer it. Form hypotheses and devise tests to determine whether those hypotheses are true or false, or to what extent you can say they're true or false if you can't get an exact answer.

Even if you answer one small question you'll be closer to understanding how the whole machine works.

If it helps, we're really asking you to use the <a href="http://en.wikipedia.org/wiki/Scientific_method">scientific method</a> to investigate how this opaque system called "a web application" operates.

Form a hypothesis. Devise an experiment that could potentially contradict that hypothesis. Run the experiment. Does it confirm or contradict your hypothesis?

If you do this enough, you'll be very very clear on what you understand and what you don't understand, and you'll have a list a mile long of both things to go investigate but also a framework in which to investigate them.
<h3>Submit!</h3>
Having at least partially answered a few of your own questions, submit your gist!
