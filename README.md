To reproduce:

    $ sudo docker run -ti --entrypoint /bin/bash l.gcr.io/google/bazel:1.2.1 -c "git clone https://github.com/gorilych/rules_nodejs_bug1.git; cd rules_nodejs_bug1; bazel run @nodejs//:yarn"

Example:


```
$ sudo docker run -ti --entrypoint /bin/bash l.gcr.io/google/bazel:0.28.0 -c "git clone https://github.com/gorilych/rules_nodejs_bug1.git; cd rules_nodejs_bug1; bazel run @nodejs//:yarn"
Cloning into 'rules_nodejs_bug1'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), done.
Checking connectivity... done.
Extracting Bazel installation...
Starting local Bazel server and connecting to it...
INFO: Analyzed target @nodejs//:yarn (2 packages loaded, 3 targets configured).
INFO: Found 1 target...
Target @nodejs_linux_amd64//:bin/yarn_node_repositories up-to-date (nothing to build)
INFO: Elapsed time: 19.276s, Critical Path: 0.09s
INFO: 0 processes.
INFO: Build completed successfully, 1 total action
INFO: Build completed successfully, 1 total action
Running yarn --cwd /rules_nodejs_bug1
yarn install v1.16.0
info No lockfile found.
[1/4] Resolving packages...
[2/4] Fetching packages...
info fsevents@1.2.9: The platform "linux" is incompatible with this module.
info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
[3/4] Linking dependencies...
[4/4] Building fresh packages...
[1/2] ⠂ bcrypt
error /rules_nodejs_bug1/node_modules/bcrypt: Command failed.
Exit code: 1
Command: node-pre-gyp install --fallback-to-build
Arguments:
Directory: /rules_nodejs_bug1/node_modules/bcrypt
Output:
internal/modules/cjs/loader.js:670
    throw err;
    ^

Error: Cannot find module '../'
    at Function.Module._resolveFilename (internal/modules/cjs/loader.js:668:15)
    at Function.Module._load (internal/modules/cjs/loader.js:591:27)
    at Module.require (internal/modules/cjs/loader.js:723:19)
    at require (internal/modules/cjs/helpers.js:14:16)
    at Object.<anonymous> (/rules_nodejs_bug1/node_modules/bcrypt/node_modules/.bin/node-pre-gyp:15:20)
    at Module._compile (internal/modules/cjs/loader.js:816:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:827:10)
    at Module.load (internal/modules/cjs/loader.js:685:32)
    at Function.Module._load (internal/modules/cjs/loader.js:620:12)
    at Function.Module.runMain (internal/modules/cjs/loader.js:877:12)
```

