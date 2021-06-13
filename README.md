# OvrPlatformUtilAction
This uses a docker image with WineHQ to run ovr-platform-util.exe

**commands** gets passed as arguments to ovr-platform-util

This relies on a Repository secret named OCULUS_TOKEN, you can get this from the API page of your developer dashboard. 
It should look like:  "OC|123456789012345|1234567890abcdef1234567890"

> Make sure you surround it with double quotes! Otherwise it will leak into your logs


Example Usage:

```
- name: Upload to Oculus

        uses: jmschrack/OvrPlatformUtilAction@v1
        with:
          commands: upload-rift-build -a appID -t ${{ secrets.OCULUS_TOKEN }} -d pathToBuildFolder -l pathToBuildExe -c chanelName -v versionNumber

```

If you are using the gameci/builder action, you can use the version it outputs in the build step.

```
${{ steps.buildStep.outputs.buildVersion}}
```