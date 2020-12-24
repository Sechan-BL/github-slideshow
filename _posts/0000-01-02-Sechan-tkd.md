from functools import wraps

def ensure_first_arg_is(val):
	def inner(fn):
		@wraps
		def wrapper(*args, **kwargs):
			if args and args[0] != val:
				return f"First arg needs to be {val}"
			return fn(*args, **kwargs)
		return wrapper
	return inner


@ensure_first_arg_is("Sechan")
def fav_person(*person):
	print(person)

print(fav_person("Sechan", "Nandan"))
print(fav_person("Dhanush", "Lohith"))

@ensure_first_arg_is(62)
def add_to_num(num1, num2):
	return num1 + num2

print(add_to_num(62,57))
print(add_to_num(31,143))   
    
