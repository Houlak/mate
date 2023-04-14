# Mate 🧉

https://user-images.githubusercontent.com/26576696/232107069-8082d2b1-30a6-4f25-a5ff-2b5c992f6fb8.mov

Mate is a macOS application designed to help developers view their logs in a more user-friendly and informative way.
With Mate, you can easily and quickly navigate through your logs and find the information you need to troubleshoot issues and optimize your code.

Upload your log file and that's it! You are ready to speed up your debugging process.
Search for specific messages, filter your logs by many options, and even sort them!

Mate helps you work smarter and faster. 😎

You can download it for free in the Mac App Store.

## Requirements

MacOS 13.0+ (Ventura).

## How does it works?

- Upload your logs file to Mate 🧉. Psss: if you’re developing an iOS app, you can use [HKLogger](https://github.com/Houlak/hklogger) in it, 
which is a library that creates and handle all the logging logic for you. Besides, it works perfectly with Mate!
- Visualize your logs as you usually do in your IDE’s console but with all the extra power that Mate provides.
- Continue with your debugging process. Every time that your log file is updated, Mate will render the new log entries automatically!

## What format must the logs follow?

`{TIMESTAMP} - [{SEVERITY}] [{TYPE}] {OPTIONAL METADATA}: {MESSAGE}^^^`

- **TIMESTAMP |** The date must follow this format: yyyy-mm-ddThh:MM:ss.
- **SEVERITY |** The log severity can be any of these values: `INFO`, `DEBUG`, `WARNING`, `ERROR`.
- **TYPE |** The log type can be any of these values: `ANALYTICS`, `NETWORKING`, `TRACE`, `HEALTH`, `DEFAULT`.
- **METADATA |** This field is optional, but could be useful if you want to add extra information from the log itself.
  In case you decide to include it, it has to follow the following format:
  `[THREAD] [FILE] [FUNCTION] [LINE]`.
- **MESSAGE |** Include whatever you want regarding the log you've added. 
  Bonus track: if any of your logs has a `NETWORKING` type, you could format the messsage like this, in order to be properly rendered in Mate 🧉:
  ```
  { 
    "method": String,
    "path": String,
    "request": { "headers": { ... }, "body": {... } },   # Headers and body are optionals
    "response": { "status": Integer, "headers": { ... }, "body": { ... } }   # Headers and body are optionals
  }
  ```

Obs: It's necessary to add `^^^` at the end of each log, because this string will work as a separator for all the logs within the file uploaded.

Here is an example of how your log file could look like:
```
2023-01-1T14:00:00 - [INFO] [TRACE] [main] [Logger.swift] [logMessage()] [Line 100]: The app has started^^^
2023-01-1T14:05:00 - [INFO] [ANALYTICS] [<NSThread: 0x6000015d82c0>{number = 10, name = (null)}] [Logger.swift] [logMessage()] [Line 100]:
Login button tapped^^^
2023-01-1T14:05:45 - [DEBUG] [NETWORKING]:
{
    "method": "GET", "path": "api/test-endpoint", "request": { 
        "headers": { "Authorization": "dummy token" }
    },
    "response": {
        "statusCode": 404,"body": {"errorCode": "404", "message": "Account not found"}
    }
}^^^
2023-01-1T14:07:30 - [WARNING] [HEALTH]: Network request failed with status code 404^^^
```

You can download an example from `Resources/Tests.log`

## FAQ
### Can I use a custom syntax for the log file?
Not yet, but stay tuned. We have planned to include this feature in the second version. 🤓

### Did you found a bug or want to submit a new feature request?
Please submit an issue and we'll take a look as soon as posible!
