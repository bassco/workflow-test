# workflow-test

Test semantic-release tags and docker tagging metadata

The release job has the reference of the merge commit 33555f7 i.s.o. b8346f1 which contains the actual tags. The `'[skip ci]'` does not create another workflow, as expected, but do we need to run again? Or, can we force the pulling of the newly created tag from the release task?

Lets' find out....

The SEM_REL_TOKEN did not have access to comments and issues to update the tag number that the pr/issue referred to. This was fixed.

The semantic-release workflow commit message is not triggering the tag workflow for the `push tag` event. Let's test removing the `[ci skip]` value....

The PAT changes were successful
The trigger has still not triggered.....

Changed the tags string - did not trigger the post-release

For 1.0.7 release...

- PAT: Added Workflow read-write access
- changed concurrency
- added branches main to the push event
- added event debugging statuses
- added SEM_REL_TOKEN to the actions/checkout for release
- change the semantic-release token to GH_TOKEN (even though it is using the PAT)
- the ref in the actions for the post-release is `main` and not a tag :(

Manually deleting and pushing a tag works - but you may need to change the releases tag in the UI if you force-push. The workflow will have a stale reference.

For 1.0.10

Set GH_TOKEN and GITHUB_TOKEN env vars for the release workflow for semantic-release. We just need get the correct the correct token to use so that the workflow for post-release can be triggered with the correct auth mechanism.

Ok, so 1.0.12 was successful and the tag workflow for post-release did run! Finally.

Now to test if `[skip ci]` has any bearing on the behaviour in github.

The workflow for tags for 1.0.13 did not run :(
Reverting the change so that we have a good working example.
