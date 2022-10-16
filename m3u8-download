#!/usr/bin/env bash

set -euo pipefail

# Title: m3u8-download
# Description: Downloads video file from an m3u8 address.
# Author: William Chanrico
# Date: 08-Nov-2017

# Depends on:
#   - ffmpeg
#   - tput

echo "Start m3u8-download!"

m3u8_address="${1:?'usage: m3u8-download M3U8_ADDRESS {OUTPUT_FILENAME}'}"
m3u8_filename=$(basename "$m3u8_address")
output_filename="${2:-$m3u8_filename}.mp4"

echo "Download $(tput bold)${m3u8_filename}$(tput sgr0) as $(tput bold)${output_filename}$(tput sgr0)"

# Whether to overwrite existing file
if [[ -e "${output_filename}" ]]; then
	read -r -p "Overwrite $(tput bold)${output_filename}$(tput sgr0)? [y/N] " input

	[[ ! "$input" =~ [yY] ]] && exit;
fi

clean_output_counter=0

ffmpeg -y -hide_banner -loglevel info -i "$m3u8_address" -c copy -bsf:a aac_adtstoasc "$output_filename" 2>&1 \
	| while read -r OUTPUT || [ -n "$OUTPUT" ]; do

	# Clean stdout and stderr every 4th line
	if [[ "$clean_output_counter" -eq 4 ]]; then
		while [[ "$clean_output_counter" -gt 0 ]]; do
			tput cuu1;
			tput el;
			clean_output_counter=$(( clean_output_counter - 1 ));
		done
	fi
	echo "${OUTPUT:0:$(tput cols)}"
	clean_output_counter=$(( clean_output_counter + 1 ));

done

echo "Finish m3u8-download!"
