# sem_ver_test

git init
// git config core.sshCommand "ssh -i C:/Users/Andrey_Lakhmanets/.ssh/id_ed25519_github"
npm init -> will create package.json
npm install --save-dev semantic-release


npm install @semantic-release/git -D
npm install @semantic-release/changelog -D


npx semantic-release-cli setup
npx semantic-release

npx semantic-release --ci=false --debug=true --dry-run=true


# Drawbacks
1. Need to specify git url - can't work locally
2. Need to specify npm registry

# questions
1. sync back to develop ??? - was solved by custom script.
2. automatic release branches - V
3. getting current version - saw via exec plugin - https://github.com/semantic-release/exec - "publishCmd": "./publish.sh ${nextRelease.version} ${options.branch} ${commits.length} ${Date.now()}"

https://github.com/KengoTODA/gradle-semantic-release-plugin/blob/master/src/prepare.ts
setting version

4. getting current version from develop branch
5. auto commit tools, lick cli-cz, commitizen, etc - commit via dialog https://github.com/commitizen/cz-cli
6. How to push branch artifacts?

plugins
https://github.com/semantic-release/semantic-release/blob/master/docs/extending/plugins-list.md


https://stackoverflow.com/questions/60566805/getting-next-tag-version-using-semantic-releases
 ["@semantic-release/exec", {
  "prepareCmd": "./update-version.sh ${nextRelease.version}",
}],

npx semantic-release --dryRun | grep -oP 'Published release \K.*? '


npx semantic-release --ci=false --debug=false --dry-run=false --plugins=@semantic-release/commit-analyzer,@semantic-release/release-notes-generator,@semantic-release/exec


test commit
another change
one more
more
test commit

test again

next 
another change
test
test
testagain




aaa



aaa






```json
{
  "name": "sem_ver_develop_test",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/SpikeVlg/sem_ver_develop_test.git"
  },
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/SpikeVlg/sem_ver_develop_test/issues"
  },
  "homepage": "https://github.com/SpikeVlg/sem_ver_develop_test#readme",
  "release": {
    "branches": [
      "+([0-9])?(.{+([0-9]),x}).x",
      "master",
      "next",
      "next-major",
      {
        "name": "develop",
        "prerelease": true,
        "channel": "develop"
      }
    ],
    "plugins": [
      "@semantic-release/commit-analyzer",
      "@semantic-release/release-notes-generator",
      [
        "@semantic-release/changelog",
        {
          "changelogFile": "CHANGELOG.md"
        }
      ],
      ["@semantic-release/exec", {
        "generateNotesCmd": "echo -n \"${nextRelease.version}\" && test.bat ${nextRelease.version} ${options.branch} ${commits.length} ${Date.now()}"
      }],
      [
        "@semantic-release/git",
        {
          "assets": [
            "dist/**/*.{js,css}",
            "docs",
            "package.json",
            "README.md",
            "CHANGELOG.md"
          ],
          "message": "chore(release): ${nextRelease.version} [skip ci]\n\n${nextRelease.notes}"
        }
      ]
    ]
  },
  "devDependencies": {
    "@semantic-release/changelog": "^5.0.1",
    "@semantic-release/exec": "^5.0.0",
    "@semantic-release/git": "^9.0.0"
  }
}

```