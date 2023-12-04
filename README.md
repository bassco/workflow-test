# workflow-test

Test semantic-release tags and docker tagging metadata

The release job has the reference of the merge commit 33555f7 i.s.o. b8346f1 which contains the actual tags. The `'[skip ci]'` does not create another workflow, as expected, but do we need to run again? Or, can we force the pulling of the newly created tag from the release task?

Lets' find out....
