# HLS downloader
This is a library to support downloading a m3u8 file. All TS segments will be downloaded into a folder and then joined into a single TS file. The default file name is `video.ts`


### Features:
* Concurrent download segments with multiple http connections
* Decrypt HLS-encoded segments
* Auto-retry download
* Display downloading progress bar
* Record a live stream video


### Todo:
* Allow adding http headers

### How to integrate this library into your code

Get the library
```
go get github.com/trong/hlsdl
```
then import it to your code.
```
import "github.com/trong/hlsdl"
```

Sample:

```go
package main

import (
	"fmt"

	"github.com/trong/hlsdl"
)

func main() {
	hlsDL := hlsdl.New("https://bitdash-a.akamaihd.net/content/sintel/hls/video/1500kbit.m3u8", nil, "download", 64, true, "")
	
	filepath, err := hlsDL.Download()
	if err != nil {
		panic(err)
	}

	fmt.Println(filepath)
}

```

### How to build a console application

Build for linux
```
make build-linux
```

Build for windows
```
make build-windows
```

Run the application

```
./bin/hlsdl --help
```

```
./bin/hlsdl -u https://bitdash-a.akamaihd.net/content/sintel/hls/video/1500kbit.m3u8 -d download -w 10
```

![example](example/hlsdl.gif)

Record a live stream video

```
./bin/hlsdl --url "http://cdn1.live-tv.od.ua:8081/bbb/bbbtv-abr/bbb/bbbtv-720p/chunks.m3u8?nimblesessionid=62115268" --record true
```

## Get prebuild here https://github.com/trong/hlsdl/releases *
