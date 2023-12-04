# workflow-test

Test semantic-release tags and docker tagging metadata

The release job has the reference of the merge commit 33555f7 i.s.o. b8346f1 which contains the actual tags. The `'[skip ci]'` does not create another workflow, as expected, but do we need to run again? Or, can we force the pulling of the newly created tag from the release task?

Lets' find out....

The SEM_REL_TOKEN did not have access to comments and issues to update the tag number that the pr/issue referred to. This was fixed.

The semantic-release workflow commit message is not triggering the tag workflow for the `push tag` event. Let's test removing the `[ci skip]` value....

The PAT changes were successful
The trigger has still not triggered.....

Changed the tags string
