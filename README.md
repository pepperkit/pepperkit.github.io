# PepperKit
A set of small unrelated tools, each of which provides a little help for Java developers - season your code with the open source pepper!

For now pepperkit includes:

## Retry
Simple and lightweight retry library for Java, it helps you transparently retry failed operations.

### Example

```
import static io.github.pepperkit.retry.Retry.retry;

    retry(3)
        .backoff(new BackoffFunction.Exponential())
        .delay(Duration.ofMillis(500))
        .maxDelay(Duration.ofSeconds(3))
        .handle(HttpServiceUnavailable.class)
        .run(()->{
            webClient.get("https://some.example.com/v1/resource");
            // webClient.get() throws HttpServiceUnavailable exception
            // e.g. try to get this resource 3 times when the HttpServiceUnavailable exception has occurred
            // we have some assumption, this service can be available later...
        });
```
### Dependecy
retry:1.0.0 has been releaseed and available
#### Maven
```xml
<dependency>
    <groupId>io.github.pepperkit</groupId>
    <artifactId>retry</artifactId>
    <version>1.0.0</version>
</dependency>
```

#### Gradle
```shell
implementation 'io.github.pepperkit:retry:1.0.0'
```

[Open in GitHub](https://github.com/pepperkit/retry)

## CoreNLP Stop Words Annotator
Annotator for CoreNLP library, allows to add the set of rules or/and the words themselves, which should be filtered out in the CoreNLP pipeline processing.

[Open in GitHub](https://github.com/pepperkit/corenlp-stop-words-annotator)
