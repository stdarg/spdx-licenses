spdx-licenses
=============

A simple module to determine if a license id is a valid SPDX license and if it
is, get the full name and a flag indicating if the license is OSI approved.

Each license entry has the following information:

* name - The full name of the license, e.g. &quot;Academic Free License v3.0&quot;
* id - The abbreviated id you used to acquire the license, e.g. &quot;AFL-3.0&quot;
* OSIApproved - A boolean flag that is true when the license is OSI approved.

An exmaple license follows:

```JSON
    "MIT": {
        "name": "MIT License",
        "id": "MIT",
        "OSIApproved": true
    }
```

## Example usage

```javascript
    var spdxLicenses = require('spdx-license');
    var target = 'LGPL-3.0+';
    var license = spdxLicenses.spdx(target);

    if (license) {
        console.log('We are working with Software Package Data Exchange® version ',
            spdxLicenses.version);
        console.log('The full name for "LGPL-3.0+" is: '+
            spdxLicenses.spdx('LGPL-3.0+').name);

        if (spdxLicenses.spdx('LGPL-3.0+').OSIApproved)
            console.log('The license is OSDI approved.');
        else
            console.log('The license is not OSDI approved.');
    } else {
        console.error('There is no such license as '+target);
    }
```

The above results in the following output:

    We are working with Software Package Data Exchange® version  1.19
    The full name for "LGPL-3.0+" is: GNU Lesser General Public License v3.0 or later
    The license is OSDI approved.

### version
The version of the SPDX License List from https://spdx.org/licenses/ - This is 
a literal non-semver-compliant string, e.g. "1.19".

### spdx(id)
Get info on a license for a given license id. And, if not a valid SPDX license
id, return false.

#### Param:
* **String** *id* The SPDX license id, e.g. &quot;MIT&quot;, &quot;Apache-2.0&quot;, etc.

#### Returns:
* **Object|Boolean** Returns an object with the info on the licese or false if there is no such license id.

