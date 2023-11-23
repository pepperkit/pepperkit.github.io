# Git Hooks Maven Plugin
Maven plugin for easy git hooks configuration.

## Usage
Add the plugin into your `pom.xml`, configure the hooks, and set the execution to install the hooks each time
the project is rebuild. Be aware that for hooks to be installed to git, any `mvn` goal should be first executed,
like `compile` or `test`. It means that after editing git-hooks-maven-plugin configuration in `pom.xml`,
it's necessary to manually run `mvn compile` or any other maven goal, on the initializing step of which git hooks will be installed.

The example with *pre-commit* and *pre-push* hooks configured, will look like this:
```xml
<plugins>
    <plugin>
        <groupId>io.github.pepperkit</groupId>
        <artifactId>git-hooks-maven-plugin</artifactId>
        <version>1.1.0</version>
        <executions>
            <!-- It will automatically trigger `init` goal at each initialize project maven phase. -->
            <execution>
                <goals>
                    <goal>initHooks</goal>
                </goals>
            </execution>
        </executions>
        <configuration>
            <hooks>
                <pre-commit>mvn -B checkstyle:checkstyle</pre-commit>
                <pre-push>mvn -B test</pre-push>
            </hooks>
        </configuration>
    </plugin>
</plugins>
```

Hook's content is any command line script, which is considered successful if exit code is equal to `0`, and not otherwise.
If execution of the script is successful, git action will be proceeded, if not - it will be cancelled.

[Open in GitHub](https://github.com/pepperkit/git-hooks-maven-plugin)
