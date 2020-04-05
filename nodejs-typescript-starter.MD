## Nodejs Typescript Starter

* git clone 的 options `--depth` 有什么用？

  > Create a shallow clone with a history truncated to the specified number of commits.

* vs code 的 task 系统可以将部分快捷键映射到部分脚本命令上
  1. 通过 ctrl(cmd) + shift + p 打开 task 管理
  2. 通过 configure task 定义 task，并绑定到特定的脚本
  3. 通过 ctrl(cmd) + shift + b 运行 build 脚本

* `.d.ts` 类型定义文件 
  * 一般来说，都可以在 `node_modules/@types/*` 中找到
  * 如果没有，可以在本地使用一个特定的文件夹进行类型定义，或者类型增强 

* Summary of `.d.ts` management
1. After installing any npm package as a dependency or dev dependency, immediately try to install the .d.ts file via @types.
2. If the library has a .d.ts file on DefinitelyTyped, the install will succeed and you are done. If the install fails because the package doesn't exist, continue to step 3.
3. Make sure you project is configured for supplying your own d.ts files
4. Try to generate a .d.ts file with dts-gen. If it succeeds, you are done. If not, continue to step 5.
5. Create a file called <some-library>.d.ts in your types folder.
6. Add the following code:
```typescript
declare module "<some-library>";
```
7. At this point everything should compile with no errors and you can either improve the types in the .d.ts file by following this guide on authoring .d.ts files or continue with no types.
8. If you are still having issues, let me know by sending me an email or pinging me on twitter, I will help you.