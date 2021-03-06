<p align="center">
    <a href="http://kituranext.org/">
        <img src="https://raw.githubusercontent.com/Kitura-Next/Kitura/master/Sources/Kitura/resources/kitura-bird.svg?sanitize=true" height="100" alt="Kitura">
    </a>
</p>


<p align="center">
    <a href="https://www.kituranext.org/learn/">
    <img src="https://img.shields.io/badge/docs-kitura-1FBCE4.svg" alt="APIDoc"></a>
    <a href="https://github.com/Kitura-Next/LoggerAPI/actions?query=workflow%3ASwift+MacOS">
    <img src="https://github.com/Kitura-Next/LoggerAPI/workflows/Swift%20MacOS/badge.svg"></a>
    <a href="https://github.com/Kitura-Next/LoggerAPI/actions?query=workflow%3ASwift+Ubuntu">
    <img src="https://github.com/Kitura-Next/LoggerAPI/workflows/Swift%20Ubuntu/badge.svg"></a>
    <img src="https://img.shields.io/badge/license-Apache2-blue.svg?style=flat" alt="Apache 2">
    <a href="http://swift-at-ibm-slack.mybluemix.net/">
    <img src="http://swift-at-ibm-slack.mybluemix.net/badge.svg" alt="Slack Status"></a>
</p>

# LoggerAPI

A logger protocol that provides a common logging interface for different kinds of loggers. In addition, a class with a set of static functions for logging within your code is provided.

[Kitura](https://github.com/Kitura-Next/Kitura) uses this API throughout its implementation when logging.

## Usage

#### Add dependencies

Add the `LoggerAPI` package to the dependencies within your application’s `Package.swift` file. Substitute `"x.x.x"` with the latest `LoggerAPI` [release](https://github.com/Kitura-Next/LoggerAPI/releases):

```swift
.package(url: "https://github.com/Kitura-Next/LoggerAPI.git", from: "x.x.x")
```
Add `LoggerAPI` to your target's dependencies:
```swift
.target(name: "example", dependencies: ["LoggerAPI"]),
```

#### Import package

```swift
import LoggerAPI
````

#### Log messages

Add log messages to your application:
```swift
Log.warning("This is a warning.")
Log.error("This is an error.")
```

#### Define a logger

You need to define a `logger` in order to output these messages. You may wish to write your own `Logger` implementation, or you can use `HeliumLogger` that writes to standard output:
```swift
import LoggerAPI
import HeliumLogger

let myLogger = HeliumLogger(.info)
Log.logger = myLogger
```
You can find out more about HeliumLogger [here](https://github.com/Kitura-Next/HeliumLogger/blob/master/README.md).

#### Logging messages to swift-log

You can direct your log messages to be logged via [swift-log](https://github.com/apple/swift-log) by setting the `swiftLogger` property:
```swift
import LoggerAPI
import Logging

let myLogger = Logging.Logger(label: "myLogger")
myLogger.logLevel = .notice
Log.swiftLogger = myLogger
```
If both `logger` and `swiftLogger` are set, then log messages will be sent to both logging backends. The log level configured for a LoggerAPI Logger and a swift-log Logger are independent, so may be used to log at different levels.

Note that because the hierarchy of log levels defined by LoggerAPI and swift-log is slightly different, a mapping is defined between the levels. See the documentation for `Log.isLogging()` for details.

## Swift version
Requires **Swift 5.1** or newer. You can download this version of the Swift binaries by following this [link](https://swift.org/download/). Compatibility with other Swift versions is not guaranteed.

## API documentation

For more information visit our [API reference](http://kitura-next.github.io/LoggerAPI/).

## Community

We love to talk server-side Swift, and Kitura. Join our [Slack](http://swift-at-ibm-slack.mybluemix.net/) to meet the team!

## License

This library is licensed under Apache 2.0. Full license text is available in [LICENSE](https://github.com/Kitura-Next/LoggerAPI/blob/master/LICENSE.txt).
