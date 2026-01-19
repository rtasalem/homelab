#!/bin/bash

while true; do
  echo "Enter the collection date (YYYY-MM-DD), or type 'exit' to stop:"
  read COLLECTION_DATE

  if [[ "$COLLECTION_DATE" == "exit" ]]; then
    echo "Exiting..."
    break
  fi

  echo "Enter bin colours that will be collected on this date (separated by space e.g. 'blue green'):"
  read -a BIN_COLOURS

  JSON_BIN_COLOURS=$(printf '%s\n' "${BIN_COLOURS[@]}" | jq -R . | jq -s .)

  python src/data/backfill.py "$COLLECTION_DATE" "$JSON_BIN_COLOURS"

  echo "----------"
done
