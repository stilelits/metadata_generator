# metadata_generator
This is a working repository for a simple standalone script that generates random database metadata. It will be substantially reworked as I refine my understanding of the proper metadata format, but right now it generates a JSON file with the following structure:


``` JSON
{
 "databaseName":"DATABASE_eBmB1CdZ",
 "createdAt":<TIMESTAMP>,
 "cols":{
  "count":<INT>,
  "items":[
   {
    "id":0,
    "name":"COLUMN_xEhq3wDv"
   },
   ...
  ],
 },
 "changeLog":{
  "count":<INT>,
  "items":[
   {
    "id":0,
    "timestamp":<TIMESTAMP>,
    "name":"CHANGE_0"
   },
   ...
  ]
 }
}
```

The names of the columns and the database are randomized alphanumeric strings. The "createdAt" timestamp is just the current time, and each changeLog timestamp is randomized to be between one minute and two days after the previous change. All of these parameters are adjustable within the script, and I expect the structure itself to completely change over the next few weeks, but right now it serves as a simple proof-of-concept for generating random data in a controlled format.

# Usage

1. Download the .wsh file to any folder you have write access, on a Windows machine.
2. Double-click the file to run it using the WScript engine.

It will generate one file in the same folder, with a name like "2025_06_03_15_53_59_173_metadata.json" based on the current time. Note that the timestamp is UTC, and it includes milliseconds, so there should never be a filename conflict, unless two copies of the script are somehow running at the exact same instant. I would highly recommend putting this in a folder by itself, so that the output files do not clutter up any folder with other types of file in it.
