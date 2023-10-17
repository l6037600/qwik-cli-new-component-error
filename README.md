In [Utilities section](https://qwik.builder.io/docs/project-structure/#utilities) on project structure page, it says by running this command:

<pre>pnpm qwik new button</pre>

It throws an error:

<pre>TypeError [ERR_INVALID_ARG_TYPE]: The "path" argument must be of type string. Received undefined</pre>

I checked the source code. In my local running environment, (cli.cjs)at line 3034`template.relative` is `undefined`.

when i specify `template.relative` value, A new error has appeared:
<pre>(cli.cjs)at line 3049: await import_node_fs7.default.promises.writeFile(fileOutput, templateOut, { encoding: "utf-8" });
Error: EISDIR: illegal operation on a directory, open 'D:\xxx\qwik-xxx\src\components\button'
</pre>

Then I modified the code from `fileOutput` to `${fileOutput}/index.tsx` and the error disappeared.
I also tried changing the dependency package version
I don’t know if it’s due to my local operating environment, incompatible versions of dependent packages, or other reasons

