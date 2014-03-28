**Developing Backbone.js Applications** by *Addy Osmani*

If you want to receive a notification when a Backbone model changes you can bind a listener to the model for its change event. A convenient place to add listeners is in the initialize() function as shown below:var Todo = Backbone.Model.extend({ // Default todo attribute values defaults: { title: '', completed: false }, initialize: function(){ console.log('This model has been initialized.'); this.on('change', function(){ console.log('- Values for this model have changed.'); }); } });

---

You may also use double curly brackets (i.e {{}}) (or any other tag you feel comfortable with) in Microtemplates. In the case of curly brackets, this can be done by setting the Underscore templateSettings attribute as follows:_.templateSettings = { interpolate : /\{\{(.+?)\}\}/g };

---

A typical server-side MVC implementation implements the Front Controller design pattern. This pattern layers an MVC stack behind a single point of entry. This single point of entry means that all HTTP requests (e.g., http://www.example.com, http://www.example.com/whichever-page/, etc.) are routed by the server’s configuration to the same handler, independent of the URI

---

