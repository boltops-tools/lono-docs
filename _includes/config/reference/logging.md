log.root | The root folder where logs are written to. | log
logger | Logger instance to use. | Logger.new($stderr)
logger.formatter | Logger Formatter to use. See [Formatter](https://ruby-doc.org/stdlib-2.7.1/libdoc/logger/rdoc/Logger/Formatter.html) for interface. | [Ufo::Logger::Formatter](https://github.com/boltops-tools/ufo/blob/master/lib/ufo/logger/formatter.rb)
logger.level | Logger level | info