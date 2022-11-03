## the view page with rails:

<h1>New Post</h1>

<h3>Post Form</h3>

<%= form_tag posts_path do %>
  <label>Post title:</label><br>
  <%= text_field_tag :title %><br>

  <label>Post Description</label><br>
  <%= text_area_tag :description %><br>

  <%= submit_tag "Submit Post" %>
<% end %>

<%= params.inspect %>

## the view page as html adding the rails' form_tag and authenticity_token:

<%= form_tag posts_path do %>

    <form action="<%= posts_path %>" method="POST">
    <label>Post title:</label><br>
    <input type="text" id="post_title" name="post[title]"><br>

    <label>Post description:</label><br>
    <textarea id="post_description" name="post[description]"></textarea><br>

    <input type="hidden" <%= hidden_field_tag :authenticity_token, form_authenticity_token %>
    <input type="submit" value="Submit Post">
  <% end %>
</form>



<%= params.inspect %>

## Note

With rails, the form_tag Rails helper generates a form withe the POST method by default, and it automatically renders the HTML that we were writing by hand before. We can explicitly specify what HTTP verb to use for the form_tag if we want something other than POST. For example if we wanted a GET request instead:

    <%= form_tag posts_search_path, method: :get do %>