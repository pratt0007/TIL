```cpp
from django.contrib import admin
from .models import *


admin.site.register(Emenities)
admin.site.register(Hotels)
```
<h3>When we make some model class and we want it to get register on the django administration page, then first we have to register in the admin.py file in the application and then we can make superuser to login in django administration and see the model tables that we have created. </h3>
