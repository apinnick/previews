# Preview builds

I created this repo to share preview builds with people outside Red Hat. Folders = branches.

## Preview build URLs

OpenShift: `https://apinnick.github.io/previews/<branch>/welcome/`

Asciidoc: `https://apinnick.github.io/previews/<branch>/html-single/`

Examples:

- `https://apinnick.github.io/previews/ocpdocs-123-new-feature/welcome/`
- `https://apinnick.github.io/previews/HCIDOCS-123-new-feature/html-single/`

## Generating previews

### OpenShift (Asciibinder)

Run the following command in the OCP-docs repo:

~~~
asciibinder && BRANCH=$(git branch --show-current) && cp -r _preview/openshift-enterprise/$BRANCH ../previews && cd ../previews && git add . && git commit -m "init" && git push && cd - && GITUSER=$(git config --get remote.origin.url | awk -F'[:/]+' '{print $2}') && echo -e "\nPreview build uploaded.\nPreview build URL: https://$GITUSER.github.io/previews/$BRANCH/welcome/"
~~~

If you just want to generate the preview build URL, you can run a shorter version of this command:

~~~
BRANCH=$(git branch --show-current) && GITUSER=$(git config --get remote.origin.url | awk -F'[:/]+' '{print $2}') && echo -e "\nPreview build URL: https://$GITUSER.github.io/previews/$BRANCH/welcome/"
~~~

### Asciidoc

Run the following command in the same directory as the master.adoc file:

~~~
bccutil && BRANCH=$(git branch --show-current) && cp -r build/tmp/en-US/ ~/previews/$BRANCH/ && cd ~/previews && git add . && git commit -m "init" && git push && cd - && GITUSER=$(git config --get remote.origin.url | awk -F'[:/]+' '{print $2}') && echo -e "\nPreview build uploaded.\nPreview build URL: https://$GITUSER.github.io/previews/$BRANCH/html-single/"
~~~

If you do not use `bccutil`, you can use probably use `asciidoctor` and play with the preview path. I have not tested this.