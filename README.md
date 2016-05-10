## FraSCAti binaries

This repository contains a customized version of the FraSCAti binaries (v1.4), including:

#### Scpecify classpath in components compilation
It is a common situation that projects depend on java classes not in the source folder but in external `jar` files. Compiling this projects with the original FrASCAti binaries is not possible. With these binaries, you can optionally specify a third parameter including the classpath as you would do when using `javac`.

##### Example:
```bash
$ frascati compile src server /path/to/my-external.jar:libs/another.jar
c:\> frascati compile-libs src server "C:\path\to\my-external.jar;libs\another.jar"
```

---

#### Include resources in jars
The jar file generated after compilation only contains java classes and composite files; what happened to those `.properties`, `.xml`, and `.fscript` files you had in your project? Those files are not added to the resulting `jar`. The enhanced binaries include these files for you.

__Note__: not supported on Windows yet

---

#### Use of the Remote and FScript plugins in components execution
FraSCAti allows you to execute components and turn on the FScript plugin. However, you cannot access the plugin because the Remote plugin is not activated. This is useless.

By specifying a port, the enhanced binaries turn on both the Remote and FScript plugins, so you can evaluate FScript expressions affecting the executed component.

##### Example:
```bash
$ frascati run -r 3000 helloworld-rmi-server -libpath server.jar:/path/to/my-external.jar:libs/another.jar
```

The Remote API is activated on http://localhost:3000 (the specified port).

__Note__: not supported on Windows yet
