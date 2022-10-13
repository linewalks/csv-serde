# Hive CSV Support

This work was contributed to the apache hive project. [see details here](https://cwiki.apache.org/confluence/display/Hive/CSV+Serde).


-----


This SerDe adds *real* CSV input and ouput support to hive using the excellent [opencsv](http://opencsv.sourceforge.net/) library.

## Using


### Basic Use

```
add jar path/to/csv-serde.jar;

create table my_table(a string, b string, ...)
  row format serde 'com.bizo.hive.serde.csv.CSVSerde'
  stored as textfile
;
```

### Custom formatting

The default separator, quote, and escape characters from the `opencsv` library and custom newline replacer defined by linewalks:

```
DEFAULT_NEWLINE_REPLACER_STR <br/>
DEFAULT_ESCAPE_CHARACTER \
DEFAULT_QUOTE_CHARACTER  "
DEFAULT_SEPARATOR        ,
```

You can also specify custom separator, quote, or escape characters.

```
add jar path/to/csv-serde.jar;

create table my_table(a string, b string, ...)
 row format serde 'com.bizo.hive.serde.csv.CSVSerde'
 with serdeproperties (
   "separatorChar" = "\t",
   "quoteChar"     = "'",
   "escapeChar"    = "\\",
   "newlineReplacerStr = "<br/>"
  )	  
 stored as textfile
;
```



## Building

Run `mvn package` to build.  Both a basic artifact as well as a "fat jar" (with opencsv) are produced.

### Eclipse support

Run `mvn eclipse:eclipse` to generate `.project` and `.classpath` files for eclipse.


## License

csv-serde is open source and licensed under the [Apache 2 License](http://www.apache.org/licenses/LICENSE-2.0.html).


