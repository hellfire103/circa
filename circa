#!/bin/bash

output=~/$(date +%F_%H%M%S).png
temp_screenshot=$(mktemp).png

read -p "Move cursor to center and press Enter"
eval $(xdotool getmouselocation --shell)
x_center=$X
y_center=$Y
read -p "Move cursor to edge and press Enter"
eval $(xdotool getmouselocation --shell)

gnome-screenshot -f $temp_screenshot

radius=$(bc <<<"sqrt(($X-$x_center)^2+($Y-$y_center)^2)")

convert $temp_screenshot -alpha on \( +clone -channel a -evaluate multiply 0 -draw "ellipse $x_center,$y_center $radius,$radius 0,360" \) -compose DstIn -composite -trim "$output"
