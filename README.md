# waybackurls-action
Github Action to get Wayback machine URLs for a list of (sub)domains.

Example Usage
-----

**GitHub Action running waybackurls on list of hosts**

```yaml
      - name: waybackurls
        uses: huseinayub/waybackurls-action@v1
        with:
          list: hosts.txt
          output: waybackurls.txt #optional
```


**Example workflow**: `.github/workflows/waybackurls.yml`


```yaml
name: waybackurls

on:
    schedule:
      - cron: '0 0 * * *'
    workflow_dispatch:

jobs:
  waybackurls:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-go@v3
        with:
          go-version: 1.18

      - name: waybackurls
        uses: huseinayub/waybackurls-action@v1
        with:
          list: hosts.txt

      - name: GitHub Workflow artifacts
        uses: actions/upload-artifact@v2
        with:
          name: waybackurls.txt
          path: waybackurls.txt
```

## Credits to:

This action is based on @tomnomnom's [waybackurls](https://github.com/tomnomnom/waybackurls) script.
Thanks for your generous work!