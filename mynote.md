### NOTES SPRING BOOT
```java
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
```
* Cette annotation permet de lancer notre application spring boot et de le lancer sur un port au hazard (`RANDOM_PORT`).

```java
@Autowired
TestRestTemplate restTemplate;
```
*  Cette annotation nous permet d'effectuer des requêtes HTTP vers l'application en mode test.
    * Même si **@Autowired** est une forme d'injection de dépendances Spring, il est préférable de l'utiliser uniquement dans les tests.

* On utilise restTemplate pour effectuer des requêtes GET HTTP.
* ResponseEntity est un autre objet Spring utile qui fournit des informations précieuses sur ce qui s'est passé avec notre requête.

```java
assertThat(response.getStatusCode()).isEqualTo(HttpStatus.OK);
```

* Ce bout de code pemettra d'acceder à plusieurs valeurs de la réponse.
  
  
