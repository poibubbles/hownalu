:

	def main():
		status = 1  # assume failure, assert success
		parser = argparse.ArgumentParser()
		group = parser.add_argument_group('group')
		group.add_argument('-t', '--test', help="test me")
			
		return status
		
	if __name__ == '__main__':
		sys.exit(main())

Should we use `sys.exit(1)` alone, a `logging` message, or raise some exception (implicitly providing a non-zero exit code)?

* Don't raise or catch exceptions in `main()`.

Philosophy:
* `main()` is a high level user interface that dispatches arguments to functions. Therefore informative output should be confined to `logging` (user-configurable) and `main()` should not raise or catch exceptions. If an exception is not handled by an underlying function, then it really is a problem whose ugliness should be exposed. If exceptions are expected *and* trace details are desired, expose them as `DEBUG` logs. 