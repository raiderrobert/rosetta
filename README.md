# rosetta
Lets compare programming languages and frameworks

## Frameworks

### Routing
Django

urlpatterns = [     
    url(r'^articles/2003/$', views.special_case_2003),
    url(r'^articles/(?P<year>[0-9]{4})/$', views.year_archive),
    url(r'^articles/(?P<year>[0-9]{4})/(?P<month>[0-9]{2})/$', views.month_archive),
    url(r'^articles/(?P<year>[0-9]{4})/(?P<month>[0-9]{2})/(?P<day>[0-9]{2})/$', views.article_detail),
    url(r'^articles/(?P<slug>[\w-]+)/$', views.slug_view),
]


DEP
urlpatterns = [     
    path('articles/2003/', views.special_case_2003),
    path('articles/<int:year>/', views.year_archive),
    path('articles/<int:year>/<int:month>/', views.month_archive),
    path('articles/<int:year>/<int:month>/<int:day>/', views.article_detail),
    path('articles/<string:slug>/', views.slug_view),
]




##Flask
Doesn't really have the idea of putting all your routes in one spot. So pardon the silly example.

    
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




Bottle
It's basically Flask (big surprise).

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





Pyramid
This one is kind of interesting. They don't have any built in validators. And they call their equivalent predicates, and their usage is far more board. 

config.add_route('special_case_2003', 'articles/2003/')
config.add_route('year_archive', 'articles/{year}/')
config.add_route('month_archive', 'articles/{year}/{month}/')
config.add_route('article_detail', 'articles/{year}/{month}/{day}/')
config.add_route('slug_view', 'articles/{slug}/')
config.scan()
