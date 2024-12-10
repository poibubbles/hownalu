What is "_ipython_canary_method_should_not_exist_"? - https://stackoverflow.com/q/56068348

You might see `_ipython_canary_method_should_not_exist_` if you `dir(some_object)` in [[IPython]].

According to the [StackOverflow answer](https://stackoverflow.com/a/56317537) to the question above, IPython sometimes checks for methods an object has "all on its own," but some objects use `__getattr__` to create attributes on the fly:

		def __getattr__(self, name):
			self.__dict__[name] = "new_attr"
			return self.__dict__[name]

The canary informs IPython that the object does this and therefore may not actually implement the methods in question.