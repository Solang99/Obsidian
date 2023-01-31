A context is a set of data that relates to the corutine.
ll corutine have an assocaited context so it's mean that when the scope create a corutine it'will automaticaly associate a context.


***Important element of a context are***:
	-  [[Dispatcher]] : Indicate which thread the corutine is running on
	- [[Job]]: A handle on the corutine lifecyle (so it can be used to stop a corutine)