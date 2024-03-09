# the-game

Testing github actions

sysctl -w vm.max_map_count=262144


#!/bin/bash

BUCKET_NAME="my-bucket-name"
INCLUDE_PATTERN="include-pattern/*"
EXCLUDE_PATTERN="exclude-pattern/*"

# List objects matching the include pattern
OBJECTS_TO_DELETE=$(aws s3 ls "s3://$BUCKET_NAME/$INCLUDE_PATTERN" --recursive | awk '{print $4}')

# Remove objects matching the exclude pattern
for object in $OBJECTS_TO_DELETE
do
    if [[ "$object" != $EXCLUDE_PATTERN ]]; then
        aws s3 rm "s3://$BUCKET_NAME/$object"
    fi
done

# --------------------- END --------------------------------
