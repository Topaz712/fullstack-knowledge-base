# Adding a Navigation Bar

Using bootstrap we set up our navbar for the header like so:

```
<nav class="navbar navbar-default">
  <div class="container-fluid">
    <div class="navbar-header"> //to have a navbar header
      <a href="#" class="navbar-brand">Recipe Book</a> // to make clickable header
    </div>

    <div class="collapse navbar-collapse"> //collapse feature
      <ul class="nav navbar-nav">//now in here we'll have list items and each will sit next to each other with bootstrap
        <li><a href="#">Recipes</a></li>
        <li><a href="#">Shopping List</a></li>
      </ul>
      <ul class="nav navbar-nav navbar-right">
        <li class="dropdown">
          <a href="#" class="dropdown-toggle" role="button">Manage <span class="caret"></span></a>//role is to add accessibility/not required.
          <ul class="dropdown-menu">
            <li><a href="#">Save Data</a></li>
            <li><a href="#">Fetch Data</a></li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</nav>
```
