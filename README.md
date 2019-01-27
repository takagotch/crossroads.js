### crossroads.js
---
https://github.com/millermedeiros/crossroads.js

```
npm install crossroads

node build
npm install --dev
npm test

git clone git://github.com/millermadeiroscrossroads.js.git
npm install crossroads
```

```js
crossroads.addRoute('foo');
crossroads.addRoutes('lorem/ipsum');
crossroads.routed.add(console.log, console);
function parseHash(newHash, oldHash){
  crossroads.parse(newHash);
}
hasher.initialized.add(parseHash);
hasher.changed.add(parseHash);
hasher.init();
hasher.setHash('lorem/ipsum');

var route1 = crossroads.addRoute('/news/{id}', function(id){
  console.log(id);
});
var route2 = crossroads.addRoute('/foo/{id}/:slug:');
route2.matched.add(console.log, console);
var route3 = crossroads.addRute('/foo/{id*}/edit');
var route4 = crossroads.addRoute(console.log, console);
route4.matched.add(console.log, console);
crossroads.addRoute('foo.php{?query}', function(query){
  console.log('lorem '+ query.lorem +' dolor sit '+ query.dolor);
});


var sectionRoute = crossroads.addRoute('/{section}/{id}');
function onSectionMatch(section, id){
  console.log(section +' - '+ id);
}
sectionRoute.matched.add(onSectionMatch);
crossroads.parse('/news/123');

var sectionRoute = crossroads.addRoute('/{section}/{id}');
function onSectionMatch(foo, bar, section, id){
  console.log(foo +' - '+ bar +' - '+ section +' - '+ id);
}
sectionRoute.matched.add(onSectionMatch);
crossroads.parse('/news/123', ["lorem", "ipsum"]);

var route1 = crossroads.addRoute('/news/{id}');
crossroads.bypassed.add(function(request){
  console.log(request);
});
crossroads.parse('/foo');

var route1 = crossroads.addRoute('/news/{id}');
crossroads.routed.add(function(request, data){
  console.log(request);
  console.log(data.route +' - '+ data.params +' - '+ data.isFirst);
});
crossroads.parse('/news/123');

var otherRouter = crossroads.create();
otherRouter.addRoute('/news/{id}', function(id){
  console.log(id);
});
otherRouter.parse('/news/123');

crossroads.routed.add(otherRouter.parse, otherRouter);
crossroads.bypassed.add(otherRouter.parse, otherRouter);

crossroads.normalizeFn = crossroads.NORM_AS_OBJECT;
crossroads.addRoute('/{foo}/{bar}', function(vals){
  console.log(vals.foo +' - '+ vals.bar);
});
crossroads.parse('/lorem/ipsum');

crossroads.normalizeFn = function(request, vals){
  return ['news', vals.id];
};
crossroads.addRoute('/{cat}/{id}', function(cat, id){
  console.log(cat +' - '+ id);
});
crossroads.parse('/article/123');

crossroads.shouldTypecast = true;
crossroads.addRoute('/news/{id}', function(id){
  console.log(id);
});
crossroads.parse('/news/00012');

crossroads.shouldTypecast = false;
crossroads.addRoute('/news/{id}', function(id){
  console.log(id);
});
crossroads.parse('/news/00012');

var sectionRouter = crossroads.create();
car nevRouter = crossroads.create();
sectionRouter.pipe(navRouter);
sectionRouter.parse('foo');

var sectionRouter = crossroads.create();
var navRouter = crossroads.create();
sectionRouter.pipe(navRouter);
sectionRouter.parse('foo');
sectionRoute.unpipe(navRouter);
sectionRouter.parse('bar');

var router1 = crossroads.addRoute('/news/{id}');
route1.matched.add(function(id){
  console.log('handler 1: '+ id);
});
route1.matched.add(function(id){
  console.log('handler 2:'+ id);
});
crossroads.parse('/news/123');

var route1 = crossroads.addRoute('/{section}/{date}/{id}');
route1.rules = {
  section : ['blog', 'news', '123'],
  date : /^[]{}-[]{}-[]{}$/,
  id : function(value, request, valueObj){
    if(isNaN(value)){
      return false;
    }else{
      if(+value < 100 && valuesObj.section == 'blog'){
        return true;
      }else if(valuesObj.section == 'news'){
        return true;
      }else{
        return false;
      }
    }
  },
  request_ : function(request){
    return (request != '123');
  },
  normalize_ : function(request, vals){
    return [vals.section, vals.id];
  }
};
route1.match("/foo/2011-05-04/2");
route1.match("/blog/20110504/2");
route1.match("/blob/2011-05-04/999");
route1.match("/blob/2011-05-04/2");

var route1 = crossroads.addRoute(/([\-\w]+)/([\-\w])/([\-\w])/);
route1.rules = {
  '0' : ['blog', 'news', '123'],
  '1' : /^[0-9]{4}-[0-9]{2}-[0-9]{2}$/,
  '2' : function(value, request, valuesObj){
    return ! isNaN(value);
  }
};
route1.match("/foo/2011-05-04/2");
route1.match("/blog/20110504/2");
route1.match("/blog/2011-05-04/abc");
route1.match("/blog/2011-05-04/2");

var projectsRoute = crossroads.addRoute('/project/:id:');
projectsRoute.add(console.log, console);
projectsRoute.greedy = true;
var projectDetailRoute = crossroads.addRoute('/projects/{id}', null, 2);
projectDetailRoute.add(console.log, console);
crossroads.parse('/projects');
crossroads.parse('/projects/123');

var route1 = crossroads.addRoute('/news/{id}');
route1.match('/foo/bar');
route1.match('/news/123');
route1.match('/news/foo-bar');

var route1 = crossroads.addRoute('news/{id}');
route1.interpolate({id: 123});
route1.interpolate({id: 'foo'});
```

```
```

