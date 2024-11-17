# Preview builds

## OpenShift docs

Preview build URL structure: `https://<user>.github.io/previews/<branch>/welcome`

You can run the following command to build the preview and upload it if you are in the openshift-docs repo:

~~~
$ asciibinder && BRANCH=$(git branch --show-current) && cp -r _preview/openshift-enterprise/$BRANCH ../previews && cd ../previews && git add . && git commit -m "init" && git push && cd - && GITUSER=$(git config --get remote.origin.url | sed -r 's/git@github.com://; s/\/openshift-docs.git//') && echo -e "\nPreview build uploaded.\nPreview build URL: https://$GITUSER.github.io/previews/$BRANCH/welcome/"
~~~

If you just want to generate the preview build URL, you can run a shorter version of this command:

~~~
$ BRANCH=$(git branch --show-current) && GITUSER=$(git config --get remote.origin.url | sed -r 's/git@github.com://; s/\/openshift-docs.git//') && echo -e "\nPreview build URL: https://$GITUSER.github.io/previews/$BRANCH/welcome/"
~~~

## Asciidoc

Preview build URL structure: `https://<user>.github.io/previews/<branch>/html-single`

You can run the following command to build the preview and upload it if you are in the same directory as the master.adoc file:

~~~
$ bccutil && BRANCH=$(git branch --show-current) && cp -r build/tmp/en-US/ ~/previews/$BRANCH/ && cd ~/previews && git add . && git commit -m "init" && git push && cd - && GITUSER=$(git config --get remote.origin.url | sed -r 's/^.*://; s/\/.*$//') && echo -e "\nPreview build uploaded.\nPreview build URL: https://$GITUSER.github.io/previews/$BRANCH/html-single/"
~~~
