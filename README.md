# metadata_generator
This is a working repository for a simple standalone script that generates random database metadata. It will be substantially reworked as I refine my understanding of the proper metadata format, but right now it generates a JSON file with the following structure:


``` JSON
{
 "databaseName":"DATABASE_wIkfoZOPRiwAW1qx",
 "createdAt":"2025-07-30T16:51:35Z",
 "tables":{
  "count":<5 to 10>,
  "items":[
   "id":0,
   "name":"TABLE_i7L6ISiZ",
   "cols":{
    "count":<10 to 20>,
    "items":[
     {
      "id":0,
      "name":"COLUMN_p9IcJ6fO"
      "data_type":"integer",
     },
     {
      "id":1,
      "name":"COLUMN_qLCBmwi6"
      "data_type":"varchar(50)",
     },
     ...
    ],
   },
   ...
  ],
  ...
 },
 "changeLog":{
  "count":<10 to 100>,
  "items":[
   {
    "id":0,
    "timestamp":"2025-07-31T03:37:56Z",
    "name":"CHANGE_0"
   },
   {
    "id":1,
    "timestamp":"2025-08-01T21:18:48Z",
    "name":"CHANGE_1"
   },
   ...
  ]
 }
}
```

The names of the columns and the database are randomized alphanumeric strings. It's possible, but highly unlikely, that two columns/tables could have conflicting names, but right now there is no conflict check.

The "createdAt" timestamp is just the current time, and each changeLog timestamp is randomized to be between one minute and two days after the previous change. 

The script generates between 5 and 10 tables, each one with between 10 and 20 columns. There are between 10 and 100 changes.

All of these parameters are adjustable within the script, and I expect the structure itself to completely change over the next few weeks, but right now it serves as a simple proof-of-concept for generating random data in a controlled format.

# Usage

1. Download "metadata_generator.wsh"
2. Double-click the file to run it using the WScript engine

It will generate one file in the same folder, with a name like "2025_06_03_15_53_59_173_metadata.json" based on the current time. Note that the timestamp is UTC, and it includes milliseconds, so there should never be a filename conflict, unless two copies of the script are somehow running at the exact same instant. I would highly recommend putting this in a folder by itself, so that the output files do not clutter up any folder with other types of file in it.

# Dependencies

1. An external library is loaded from http://ajax.cdnjs.com/ajax/libs/json2/20110223/json2.js in order to perform JSON stringification. This requires internet access, but it is not expected that this library will ever be unavailable. (In general, it's unwise to load external libraries like this, but it simplifies execution if the user only has to download one file.)
2. The file must be run on a Windows machine with WScript enabled, in a folder where the user has write access.

# To do

1. I need to refine my understanding of the actual structure that I'm attempting to imitate, and implement it in the generator.
2. I need to characterize what non-anomalous metadata would look like, and ensure that the generator produces it reliably.
3. I need to characterize what anomalous metadata would look like, and create functionality that will purposefully generate specific types of anomaly.
