# the-game

https://k8s-notes.s3.ap-south-1.amazonaws.com/kubernetes/w_pacc08.pdf?response-content-disposition=inline&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEPr%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCmFwLXNvdXRoLTEiRzBFAiAqHJOLDT2A1HTheHNasE58GYRHTdrgoob8ahWrB9mOkwIhAOwTxF7n8YrluborfhnvxkBMfNbLPNn6pUbbJ1nGO%2FbgKpIDCPP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQABoMMTkyMDQzMDM4NjEwIgy1n4%2FpsslNwc06kpIq5gLS%2FvqcNQLS8C98oMdrHTaXH8PNVcX0E96rYsHKpt45ouLq%2BUAAcuZLOamSM27Q8%2Fq1XCeFSROYIobKu18tYZPXpdBP7K%2BG2NmswkTnSS1BGkZWvYEWVXPa9FFd5NTl1GAjR7AxwfqpagwUVzt67sVfQLCUJC0Qv%2BrA5aEsFN0AHi1bmDxTchx%2Fx042FM8FhyWTgoaT2kpXMiz5kCiAozs01Phs%2Bqsy6V2acS0mRJ10WKMDauGGxZsBNUhk702%2Bd2%2B7JgXZgx36dgfq7zdaO5KJMyGC13uxnQmXQQS8Yr7Hj3pWWyvuUgMBxiWIVP6Q7EZALOv787A9XoZyuz5kU8o03jv60e%2B1mv3TTRP4lrK6OMZYoeDfHkUjHmKhhaJ%2Bqo9OOJO%2BuGvfUizREfq8EpRjg2q7bpJWJS%2F9SdY6sxgmeRSpwkGYQVtCJiDoiuLqUbRV01%2F15gRyCvojNBy5t05YUkJyleSBMMO2sq8GOrMCZAFxGqbcWqJ0Y%2Fn2HgypJqYmeppzVOWpoE5ChlK7oVGKfX4%2FKgC7uSUDVSyO9txrxviphznrUqCmZFafDVChe45BeXBc5%2BQZn%2BwJKvEKSF7XGXLrfq4oaCj1mRCBfyK%2Fho%2B%2Bzu9vSSc3IDM5%2Ba%2BvJVnuKzyd0CYkMg%2FJc5EaYSteCIcKv7TBPzE9b%2FnrxcPfoTiVJ1wTuVGUoH6E3Qc4dyEke8lcUVprYcel%2BmUpqbnNSz3%2B9Wr2kwKSoQs0J8f3tR81yJ1C%2BUuZ%2F9T3vFHSL3UeXi%2Fnx4z05WDnCoTwVyNpXNLhS4D9IgfnFIYuAMq5%2BXh%2BXuewxKwWImZQA8IC3ttlgUwfLFlCEr%2BU78znyv4MIvdGqTdEaIsMmcQyfOTR75zpQmZ7Vv9sU0Y1ocimGnAfZQ%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20240309T174304Z&X-Amz-SignedHeaders=host&X-Amz-Expires=300&X-Amz-Credential=ASIASZNVIG6JLQBVWXHP%2F20240309%2Fap-south-1%2Fs3%2Faws4_request&X-Amz-Signature=f42c1c5bf330e275195d65105d778c4217da4204db0b2445101169217b03c164

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
