# metadata_generator
This is a working repository for a simple standalone script that generates random database metadata. It will be substantially reworked as I refine my understanding of the proper metadata format, but right now it generates a JSON file with the following structure:


``` JSON
{
 "databaseName":"DATABASE_wIkfoZOPRiwAW1qx",
 "createdAt":"2025-07-30T16:51:35Z",
 "cols":{
  "count":<5 to 15>,
  "items":[
   {
    "id":0,
    "name":"COLUMN_p9IcJ6fO"
   },
   {
    "id":1,
    "name":"COLUMN_qLCBmwi6"
   },
   ...
  ],
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

The names of the columns and the database are randomized alphanumeric strings. It's possible, but highly unlikely, that two columns could have conflicting names, but right now there is no conflict check.

The "createdAt" timestamp is just the current time, and each changeLog timestamp is randomized to be between one minute and two days after the previous change. 

The script generates between 5 and 15 columns, and between 10 and 100 changes.

All of these parameters are adjustable within the script, and I expect the structure itself to completely change over the next few weeks, but right now it serves as a simple proof-of-concept for generating random data in a controlled format.

# Usage

1. Download "metadata_generator.wsh" to any folder where you have write access, on a Windows machine.
2. Double-click the file to run it using the WScript engine.

It will generate one file in the same folder, with a name like "2025_06_03_15_53_59_173_metadata.json" based on the current time. Note that the timestamp is UTC, and it includes milliseconds, so there should never be a filename conflict, unless two copies of the script are somehow running at the exact same instant. I would highly recommend putting this in a folder by itself, so that the output files do not clutter up any folder with other types of file in it.

# To do

1. I need to refine my understanding of the actual structure that I'm attempting to imitate, and implement it in the generator.
2. I need to characterize what non-anomalous metadata would look like, and ensure that the generator produces it reliably.
3. I need to characterize what anomalous metadata would look like, and create functionality that will purposefully generate specific types of anomaly.