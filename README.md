# tornado_sample

# Montamos el Entorno virtual
```  
virtualenv hola_mundo
cd hola_mundo
source bin/activate
cd ..
```  
# Instalamos Tornado
```
pip install tornado
```

# creamos el fichero hello_word_01.py
```
nano hello_word_01.py
```

# hello_word_01.py
```
# Marlon Falcon
import tornado.ioloop
import tornado.web 

class Index(tornado.web.RequestHandler):
    def get(self):
        #y vamos a escribir en le navegador el hola mundo
        self.write('Hola Mundo')

if __name__ == '__main__':
    #declaramos la url con la clase que arriba
    app = tornado.web.Application([
        (r'/',Index)
    ])
    app.listen(8888)
    tornado.ioloop.IOLoop.instance().start()
```


# Corremmos hello_word_01.py
```
python hello_word_01.py
```


# demo.py
```
import tornado.ioloop
import tornado.web 

class BasicRequestHandler(tornado.web.RequestHandler):
    def get(self):
        self.write('Hola Mundo')

class staticRequestHandler(tornado.web.RequestHandler):
    def get(self):
        self.render("index.html")

# localhost:8888/isEven?n=12
class queryStringRequestHandler(tornado.web.RequestHandler):
    def get(self):
        n = int(self.get_argument("n"))
        r = "add" if n % 2 else "even"
        self.write('the number' + str(n) + " is: " + r)       

if __name__ == '__main__':
    app = tornado.web.Application([
        (r'/', BasicRequestHandler) ,
        (r'/blog', staticRequestHandler) ,
        (r'/isEven', queryStringRequestHandler) ,

    ])


    app.listen(8888)
    tornado.ioloop.IOLoop.instance().start()
```
