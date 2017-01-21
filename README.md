# rosetta
Lets compare programming languages and frameworks

## Frameworks

### Routing

#### Django

```python
urlpatterns = [     
    url(r'^articles/2003/$', views.special_case_2003),
    url(r'^articles/(?P<year>[0-9]{4})/$', views.year_archive),
    url(r'^articles/(?P<year>[0-9]{4})/(?P<month>[0-9]{2})/$', views.month_archive),
    url(r'^articles/(?P<year>[0-9]{4})/(?P<month>[0-9]{2})/(?P<day>[0-9]{2})/$', views.article_detail),
    url(r'^articles/(?P<slug>[\w-]+)/$', views.slug_view),
]
```

#### .NET Core
```cs
    routeBuilder.MapRoute(
        "Special Case 2003",
        "articles/2003/");
    routeBuilder.MapRoute(
        "Year Archive",
        "articles/{year:regex(^\\d{{4}}$)}/");
    routeBuilder.MapRoute(
        "Month Archive",
        "articles/{year:regex(^\\d{{4}}$)}/{month:regex(^\\d{{2}}$)}/");
    routeBuilder.MapRoute(
        "Article Detail",
        "articles/{year:regex(^\\d{{4}}$)}/{month:regex(^\\d{{2}}$)}/{day:regex(^\\d{{2}}$)}/");
    routeBuilder.MapRoute(
        "Slug View",
        "articles/{year:regex(^\\w-}$)}/");

    var routes = routeBuilder.Build();
    app.UseRouter(routes);
   ```
### ORMs

#### Models

##### Django
```python
from django.db import models

class Book(models.Model):
    author = models.CharField(max_length=250, unique=True)
    title = models.CharField(max_length=250)
    description = models.TextField()
```

#### Create

##### Django
```python
Book.objects.create(author='Unique Name of Person', title='Sample title', text='Test')
```

#### Query

##### Django
```python
Book.objects.get(author='Unique Name of Person')
```

#### Update

##### Django
```python
book = Book.objects.get(author='Unique Name of Person')
book.text = 'Different test'
book.save()
```


## Python Frameworks and Popular Packages

### Routing

#### Django
```python
urlpatterns = [     
    url(r'^articles/2003/$', views.special_case_2003),
    url(r'^articles/(?P<year>[0-9]{4})/$', views.year_archive),
    url(r'^articles/(?P<year>[0-9]{4})/(?P<month>[0-9]{2})/$', views.month_archive),
    url(r'^articles/(?P<year>[0-9]{4})/(?P<month>[0-9]{2})/(?P<day>[0-9]{2})/$', views.article_detail),
    url(r'^articles/(?P<slug>[\w-]+)/$', views.slug_view),
]
```

#### Flask
```python   
@app.route('articles/2003/')
def special_case_2003():
	pass

@app.route('articles/<int:year>/')
def year_archive(year):
	pass

@app.route('articles/<int:year>/<int:month>/')
def month_archive(year, month):
	pass

@app.route('articles/<int:year>/<int:month>/<int:day>/')
def article_detail(year, month, day):
	pass

@app.route('articles/<string:slug>/')
def slug_view(slug):
	pass
```

#### Bottle
```python
@route('articles/2003/')
def special_case_2003():
	pass

@route('articles/<year:int>/')
def year_archive(year):
	pass

@route('articles/<year:int>/<month:int>/')
def month_archive(year, month):
	pass

@route('articles/<year:int>/<month:int>/<day:int>/')
def article_detail(year, month, day):
	pass

@route('articles/<slug:string>/')
def slug_view(slug):
	pass
```

#### Pyramid
```python
config.add_route('special_case_2003', 'articles/2003/')
config.add_route('year_archive', 'articles/{year}/')
config.add_route('month_archive', 'articles/{year}/{month}/')
config.add_route('article_detail', 'articles/{year}/{month}/{day}/')
config.add_route('slug_view', 'articles/{slug}/')
config.scan()
```
