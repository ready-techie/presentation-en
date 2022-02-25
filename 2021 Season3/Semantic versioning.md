How do you manage your software application's version?

One suggestion is [Semantic Versioning](https://semver.org/) (Semver) which is officially used at Node.js, npm

# Major.Minor.Patch

![https://blog.kakaocdn.net/dn/YzXwY/btrfUPYj9F2/MunaAi7y9735xbJqLYIth1/img.png](https://blog.kakaocdn.net/dn/YzXwY/btrfUPYj9F2/MunaAi7y9735xbJqLYIth1/img.png)

### **Major version**

- Includes incompatible API changes
- Set `Minor`, `Patch` version 0 if `Major` changes (1.2.33 -> 2.0.0)

### **Minor version**

- includes compatible API changes
- Set `Patch` 0 if Minor changes (1.2.33 -> 1.3.0)

### **Patch Versions**

- for bugfixes, not for feature updates

### 💡 Notice

- Dots are not for decimal points. Which means 1.0.10 is the later version than 1.0.2
- 1.0.0 is production release, 0.x.x means development draft
- The very first version is 0.1.0, not 0.0.1 since there's no bugfixes
- `Pre-release` adds `-` , `Build` adds `+` behind the patch version (1.0.0-alpha.1, 1.0.0+build.1)

# Version Range

You might have seen `^` or `~` prefixed version on package.json file. These represent the version range.

![https://blog.kakaocdn.net/dn/dSYZIT/btrfTKiGh3h/YImCy924NQtK2hKlo78NX1/img.jpg](https://blog.kakaocdn.net/dn/dSYZIT/btrfTKiGh3h/YImCy924NQtK2hKlo78NX1/img.jpg)

### ^ Caret

“**Compatible with version**”, will update you to all future minor/patch versions, without incrementing the major version. Allows lower versions behind the leading non-0 to be updated

- ^1.x.x: Allow minor, patch
- ^0.1.x: Allow patch update
- ^0.0.1: No updates allowed

### ~ Tilde

“**Approximately equivalent to version**”, will update you to all future patch versions, without incrementing the minor version.

Allow `patch` update if `minor` version is determined

- ~1.1.x : Allow patch update (1.1.0 <= ~1.1.x < 1.2.0)

Allow `minor` update if `minor` version is not determined

- ~2: Allow minor updates since minor version is not determined (2.0.0 <= ~2 < 3.0.0)

# npm example

[Check out](https://semver.npmjs.com/) real packages which use `SemVer`

npm i react --save: Install latest ^ (^2.0.0)

- caret became the default semver save prefix

npm i react --save-exact: Install latest (2.0.0)
