# sem_ver_develop_test


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