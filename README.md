# My Useful Commands

## Docker

```
// Build
docker build -t my-name --build-arg DOCKER_ENV=development .

// Open a shell in the image context to inspect the files
docker run -it --rm  my-name sh

```

## Find

```
// Find and delete all DS_Store files
find . -name '.DS_Store' -type f -delete // del DS Store

// Find and delete all json files
find . -name "*.json" -type f -delete // del .json

// Find and delete all empty folders
find . -type d -empty -delete // empty dir

// Diff two folders
diff ./folder1 ./folder2

// Does this work?
colordiff ./folder1 ./folder2


// Merge two folders with rsync
rsync -av ./test1/* ./test2 --ignore-existing --remove-source-files 
```

## EXIFTOOL

```
EXIF 

https://productforums.google.com/forum/#!topic/photos/mWeNs-fBPys

REMOVE ALL
exiftool -all= −overwrite_original ./

FIX DATE FROM FILENAME
exiftool "-datetimeoriginal<filename" -d “%y-%m-%d_%H-%M-%S.%%e” ./

CLONE DATES
exiftool "-filemodifydate<datetimeoriginal" "-createdate<datetimeoriginal" "-mediacreatedate<datetimeoriginal" "-trackcreatedate<datetimeoriginal" "-mediamodifydate<datetimeoriginal" "-trackmodifydate<datetimeoriginal" "-IPTC:DateCreated<datetimeoriginal" "-IPTC:DigitalCreationDate<datetimeoriginal" ./ −overwrite_original

exiftool "-alldates<filename" −overwrite_original ./
exiftool "-alldates<datetimeoriginal" ./


exiftool "-Time:all<filename" −overwrite_original ./




Update GPS
exiftool −overwrite_original_in_place -r -tagsFromFile source.jpg -gps:all .

CLONE
exiftool -TagsFromFile srcimage.jpg "-all:all>all:all" targetimage.jpg

exiftool "-alldates<filename" "-filemodifydate<filename" "-createdate<filename" "-mediacreatedate<filename" "-trackcreatedate<filename" "-mediamodifydate<filename" "-trackmodifydate<filename" ./ −overwrite_original



exiftool “-DateTimeOriginal+=5:10:2 10:48:0” DIR



Say you want to copy the EXIF header from file a.crw to a.jpg:
exiftool -TagsFromFile a.crw a.jpg
If you don't want to copy the Orientation field, then run:
exiftool -TagsFromFile a.crw --Orientation a.jpg



exiftool -fileOrder DateTimeOriginal -recurse -extension jpg -ignoreMinorErrors '-FileName<CreateDate' -d %Y-%m-%d%%-.3nc.%%e "$@"

exiftool ‘-filename=%f - %-1:D.%e’ '-directory=./no-date’ -r -if 'not $datetimeoriginal'

exiftool ‘-filename=./no-date/%f - %-1:D.%e’ -r -if 'not $datetimeoriginal'

exiftool -d "%Y-%m-%d/%Y-%m-%d_kl.%H%M%%-c -(%%f).%%e" "-filename<H264:DateTimeOriginal" filename.M2TS

exiftool -r -if 'not $datetimeoriginal' '-testname<./no-date/${filename}_${directory}.${filetypeextension}' .

exiftool -r -if 'not $datetimeoriginal' '-filename<./no-date/%f_${directory}.%e'  .

exiftool -r -if 'not $datetimeoriginal' ‘-testname<./no-date/%f_${directory}.%e'  .

exiftool -r -if 'not $datetimeoriginal' '-testname<./no-date/${filename;s/\///g}-${directory;s/\//-/g}.${filetypeextension}' . 



FINAL

exiftool -r -if 'not $datetimeoriginal' ‘-filename<./no-date/${directory;s/[ .\/]/-/g}-${filename}' . 

exiftool -r -d "%Y-%m-%d_%H-%M-%S"  '-filename<./parsed/${datetimeoriginal}___${directory;s/[ .\/]/-/g}-${filename}' ./114981850915577291693


ORGANISE 

//exiftool -if '$filename !~ /^\./' ... (remove ._)
exiftool -r -d "%Y-%m-%d"  '-filename<./parsed/${datetimeoriginal}/new-${filename}' ./Photos/


```

## FFMPEG

```
// Unknown
ffmpeg -i a -vcodec h264 -acodec mp2 b.mp4
ffmpeg -i a.mp4 -vcodec h264 -b:v 6000k -acodec mp2 b.mp4
ffmpeg -i a.mp4 -vcodec h264 -b:v 6000k -acodec mp3 b.mp4

// Convert 3GP to mp4
ffmpeg -i ./xx.3gp ./xx.mp4

// Unknown
ffmpeg -i ./climbing/2008-02-08_00-37-24-5.3gp -vf "transpose=1" ./2008-02-08_00-37-24-5.mp4 

// Fix broken metadata by reencoding
ffmpeg -i ./in.mp4 -c copy ./out.mp4
```

## Fixing NVM path

```
export NVM_DIR="$HOME/.nvm" [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```

## Get iplayer

```
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b070p5yw
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b00hn4hs
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b00hq341
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b00hvw59
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b00j1bhw
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b00j4c6b
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b00j8g9g
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b04tr9x9
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b03jrxhv
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/p01k4yt6
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b06pm7t8
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b06nxwld
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b01g98vb
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b033664m
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b0101h6w
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b02xgf5d
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b02xbj6m
get_iplayer --modes=best --get http://www.bbc.co.uk/programmes/b00zv39p

```
