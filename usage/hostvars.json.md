# hostvars.json

This json is included in the firmware directly and stores security related data needed by the bootloader.

```text
{
  "minimal_signatures_match": 3,
  "fingerprints": [
    "6a7120faa7becbfed349bfb1c8a8d530c82c7492ec65af3bedde1c37c4c4e39b"
  ],
  "build_timestamp": 1582627354
}


```

* `minimal_signatures_match` is the minimum number of signatures that must pass validation.
* `fingerprints` are used to validate the root certificate insinde the bootball.
*  `build_timestamp` is the UNIX build time of the bootloader.

