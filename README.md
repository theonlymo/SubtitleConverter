# Subtitle Converter

<p align="center">
  <img src="https://github.com/theonlymo/SubtitleConverter/assets/145556517/29362394-d84a-4b52-bad0-5b889e617040" alt=""/>
</p>

Subtitle Converter is a Swift library that allows you to convert subtitles from SRT to VTT format using a remote API.

## Features

- Convert subtitles from local files or remote URLs
- Save converted subtitles to temporary files
- Handle network errors and invalid responses
- Use async/await syntax for concurrency

## Installation

To use Subtitle Converter in your project, you need to add it as a dependency in your `Package.swift` file:

```swift

.binaryTarget(
    name: "SubtitleConverter",
    url: "https://github.com/theonlymo/SubtitleConverter/releases/download/1.0/SubtitleConverter.zip",
    checksum: "cfebc9b9f361996dcaf1c8021cc449c5cf2b90424a847ad8150dc332f1d41f19"
)
```

Then, you need to import it in your source files:

```swift
import SubtitleConverter
```

## Usage
You can use the `convert` methods to convert subtitles from either a local file path or a remote URL. Both methods return a URL of the converted subtitle file in the temporary directory. The methods are asynchronous and throw errors if something goes wrong.

```swift
// Convert subtitles from a local file path
let localFilePath = URL(fileURLWithPath: "/path/to/subtitle.srt")
do {
    let convertedFileURL = try await SubtitleConverter.convert(localFilePath: localFilePath)
    print("Converted file URL: \(convertedFileURL)")
} catch {
    print("Conversion failed: \(error)")
}

// Convert subtitles from a remote URL
let remoteURL = URL(string: "https://example.com/subtitle.srt")!
do {
    let convertedFileURL = try await SubtitleConverter.convert(remoteURL: remoteURL)
    print("Converted file URL: \(convertedFileURL)")
} catch {
    print("Conversion failed: \(error)")
}
```

## License

Subtitle Converter is licensed under the MIT License. See [LICENSE] for more details.
