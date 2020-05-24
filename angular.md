# serve
```
$ ng serve
** Angular Live Development Server is listening on localhost:4200, open your browser on http://localhost:4200/ **
```

```
$ ng serve --host 128.100.94.84
** Angular Live Development Server is listening on 128.100.94.84:4200, open your browser on http://128.100.94.84:4200/ **
```

```
$ ng config projects["oec4"].architect["serve"].options
{
  "browserTarget": "oec4:build"
}
```
```
$ ng config projects["oec4"].architect["serve"].options {port:4200}
$ ng config projects["oec4"].architect["serve"].options
{
  "port": 4200
}
```
```
$ ng config projects["oec4"].architect["serve"].options {"browserTarget": "oec4:build", "port": 4200}
Unexpected end of file.
Error: Unexpected end of file.
...
```
```
$ ng config projects["oec4"].architect["serve"].options {host:128.100.94.84}
Invalid JSON character: "9" at 0:13.
Error: Invalid JSON character: "9" at 0:13.
...
```

Manually edited angular.json to add the host and port in.
```
$ ng config projects["oec4"].architect["serve"].options
{
  "browserTarget": "oec4:build",
  "host": "128.100.94.84",
  "port": 4200
}
```
```
$ ng serve
** Angular Live Development Server is listening on 128.100.94.84:4200, open your browser on http://128.100.94.84:4200/ **
```

# update
```
$ ng update
    We analyzed your package.json, there are some packages to update:
    
      Name                               Version                  Command to update
     --------------------------------------------------------------------------------
      @angular/cdk                       7.2.2 -> 8.2.3           ng update @angular/cdk
      @angular/cli                       7.3.1 -> 8.3.21          ng update @angular/cli
      @angular/core                      7.2.4 -> 8.2.14          ng update @angular/core
      @angular/core                      7.2.4 -> 7.2.15          ng update @angular/core
      @angular/material                  7.2.2 -> 8.2.3           ng update @angular/material
      @ngrx/store                        7.2.0 -> 8.6.0           ng update @ngrx/store
      rxjs                               6.4.0 -> 6.5.3           ng update rxjs
    
    
    There might be additional packages that are outdated.
    Run "ng update --all" to try to update all at the same time.
    
$ ng update --all
                  Package "ng-packagr" has an incompatible peer dependency to "typescript" (requires ">=2.7 <3.6", would install "3.7.4")
                  Package "@angular/compiler-cli" has an incompatible peer dependency to "typescript" (requires ">=3.4 <3.6", would install "3.7.4")
                  Package "tsickle" has an incompatible peer dependency to "typescript" (requires "~3.6.4", would install "3.7.4")
                  Package "@angular/core" has an incompatible peer dependency to "zone.js" (requires "~0.9.1", would install "0.10.2")
                  Package "bootstrap" has a missing peer dependency of "jquery" @ "1.9.1 - 3".
                  Package "@angular/core" has an incompatible peer dependency to "zone.js" (requires "~0.9.1", would install "0.10.2").
                  Package "@angular-devkit/build-angular" has an incompatible peer dependency to "typescript" (requires ">=3.1 < 3.6", would install "3.7.4")
                  Package "@angular/http" has an incompatible peer dependency to "@angular/core" (requires "7.2.15", would install "8.2.14")
                  Package "ng-packagr" has an incompatible peer dependency to "typescript" (requires ">=2.7 <3.6", would install "3.7.4").
Incompatible peer dependencies found. See above.
```
```
$ sudo npm install -g typescript@latest
/usr/local/bin/tsc -> /usr/local/lib/node_modules/typescript/bin/tsc
/usr/local/bin/tsserver -> /usr/local/lib/node_modules/typescript/bin/tsserver
+ typescript@3.7.4
```
## install older version
```
$ sudo npm install -g @angular/cli
/usr/local/bin/ng -> /usr/local/lib/node_modules/@angular/cli/bin/ng

> @angular/cli@8.3.21 postinstall /usr/local/lib/node_modules/@angular/cli
> node ./bin/postinstall/script.js

npm WARN notsup Unsupported engine for @angular/cli@8.3.21: wanted: {"node":">= 10.9.0","npm":">= 6.2.0"} (current: {"node":"8.17.0","npm":"6.13.4"})
npm WARN notsup Not compatible with your version of node/npm: @angular/cli@8.3.21
npm WARN notsup Unsupported engine for @angular-devkit/core@8.3.21: wanted: {"node":">= 10.9.0","npm":">= 6.2.0"} (current: {"node":"8.17.0","npm":"6.13.4"})
npm WARN notsup Not compatible with your version of node/npm: @angular-devkit/core@8.3.21
npm WARN notsup Unsupported engine for @angular-devkit/architect@0.803.21: wanted: {"node":">= 10.9.0","npm":">= 6.2.0"} (current: {"node":"8.17.0","npm":"6.13.4"})
npm WARN notsup Not compatible with your version of node/npm: @angular-devkit/architect@0.803.21
npm WARN notsup Unsupported engine for @angular-devkit/schematics@8.3.21: wanted: {"node":">= 10.9.0","npm":">= 6.2.0"} (current: {"node":"8.17.0","npm":"6.13.4"})
npm WARN notsup Not compatible with your version of node/npm: @angular-devkit/schematics@8.3.21
npm WARN notsup Unsupported engine for @schematics/update@0.803.21: wanted: {"node":">= 10.9.0","npm":">= 6.2.0"} (current: {"node":"8.17.0","npm":"6.13.4"})
npm WARN notsup Not compatible with your version of node/npm: @schematics/update@0.803.21
npm WARN notsup Unsupported engine for @schematics/angular@8.3.21: wanted: {"node":">= 10.9.0","npm":">= 6.2.0"} (current: {"node":"8.17.0","npm":"6.13.4"})
npm WARN notsup Not compatible with your version of node/npm: @schematics/angular@8.3.21

+ @angular/cli@8.3.21
added 154 packages from 75 contributors, removed 145 packages and updated 38 packages in 19.045s

$ ng
You are running version v8.17.0 of Node.js, which is not supported by Angular CLI 8.0+.
The official Node.js version that is supported is 10.9 or greater.
```
So I have to go back to v7.3.1
```
sudo npm uninstall -g @angular/cli
sudo npm cache verify
sudo npm install -g @angular/cli@7.3.1
```
