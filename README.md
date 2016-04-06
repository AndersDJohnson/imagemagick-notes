# imagemagick-notes
Notes on ImageMagick.

## Thumbnails

Crop & center to square:
```
OUT_DIR="thumb-400"
D_W=400
D_H=400

mkdir -p "${OUT_DIR}"
find -maxdepth 1 -type f -not -iname Thumbs.db -print0 | while read -d '' -r FILE; do
  echo $FILE
  FILE_BASE=$(basename "$FILE" | cut -d. -f1)
  convert "$FILE" -thumbnail "${D_W}x${D_H}^" -gravity center -extent "${D_W}x${D_H}" "${OUT_DIR}/${FILE_BASE}.jpg"
done
```
