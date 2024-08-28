Les annotations sont une partie fondamentale du développement avec Spring Boot, simplifiant la configuration et la gestion des composants dans une application. Voici un aperçu complet des annotations les plus courantes et importantes dans Spring Boot, ainsi que leurs rôles et utilisations.

### 1. **Annotations de Base**

- **`@SpringBootApplication`**
  - **Rôle :** Marque une classe comme étant la classe principale d'une application Spring Boot. Elle combine les annotations suivantes :
    - `@Configuration` : Indique que la classe contient des définitions de beans.
    - `@EnableAutoConfiguration` : Active la configuration automatique basée sur les dépendances du classpath.
    - `@ComponentScan` : Recherche les composants Spring (`@Component`, `@Service`, `@Repository`, `@Controller`, etc.) dans le package et ses sous-packages.
  - **Utilisation :** Placez cette annotation sur la classe principale de l'application, généralement celle qui contient la méthode `main`.

  ```java
  @SpringBootApplication
  public class MyApplication {
      public static void main(String[] args) {
          SpringApplication.run(MyApplication.class, args);
      }
  }
  ```

- **`@Component`**
  - **Rôle :** Indique que la classe est un composant Spring et sera automatiquement détectée par la recherche de composants et enregistrée dans le contexte Spring.
  - **Utilisation :** Utilisé pour marquer des classes comme composants génériques (services, DAO, etc.).

- **`@Service`**
  - **Rôle :** Spécialisation de `@Component`, indique que la classe est un service métier.
  - **Utilisation :** Utilisé pour marquer des classes qui contiennent la logique métier.

- **`@Repository`**
  - **Rôle :** Spécialisation de `@Component`, indique que la classe est un DAO (Data Access Object).
  - **Utilisation :** Utilisé pour marquer des classes qui interagissent avec la base de données.

- **`@Controller`**
  - **Rôle :** Indique que la classe est un contrôleur Spring MVC, traitant les requêtes HTTP et renvoyant les réponses.
  - **Utilisation :** Utilisé pour les contrôleurs qui retournent des vues.

- **`@RestController`**
  - **Rôle :** Spécialisation de `@Controller`, indique que la classe est un contrôleur RESTful, et que les réponses des méthodes doivent être directement sérialisées dans le corps de la réponse HTTP.
  - **Utilisation :** Utilisé pour les contrôleurs RESTful qui gèrent les APIs HTTP.

- **`@RequestMapping`**
  - **Rôle :** Associe des méthodes de contrôleur avec des requêtes HTTP spécifiques.
  - **Utilisation :** Peut être utilisé pour mapper des URL aux méthodes de contrôleur.

  ```java
  @RequestMapping("/api")
  public class MyController {
      @RequestMapping("/hello")
      public String hello() {
          return "Hello, World!";
      }
  }
  ```

### 2. **Annotations de Configuration**

- **`@Configuration`**
  - **Rôle :** Indique que la classe contient des beans de configuration Spring.
  - **Utilisation :** Utilisé pour définir des beans via des méthodes annotées avec `@Bean`.

- **`@Bean`**
  - **Rôle :** Déclare un bean Spring dans une méthode d'une classe annotée avec `@Configuration`.
  - **Utilisation :** Utilisé pour définir des beans personnalisés.

  ```java
  @Configuration
  public class AppConfig {
      @Bean
      public MyService myService() {
          return new MyServiceImpl();
      }
  }
  ```

- **`@PropertySource`**
  - **Rôle :** Spécifie les fichiers de propriétés à charger dans le contexte Spring.
  - **Utilisation :** Utilisé pour charger des fichiers de propriétés externes.

  ```java
  @Configuration
  @PropertySource("classpath:application.properties")
  public class AppConfig {
  }
  ```

### 3. **Annotations pour la Gestion des Données**

- **`@Entity`**
  - **Rôle :** Indique qu'une classe est une entité JPA et doit être mappée à une table de base de données.
  - **Utilisation :** Utilisé pour marquer les classes qui représentent des tables dans la base de données.

- **`@Table`**
  - **Rôle :** Spécifie le nom de la table à laquelle l'entité est mappée.
  - **Utilisation :** Utilisé pour personnaliser le nom de la table pour une entité.

  ```java
  @Entity
  @Table(name = "users")
  public class User {
      @Id
      @GeneratedValue(strategy = GenerationType.IDENTITY)
      private Long id;
      
      private String username;
      private String password;
      
      // getters and setters
  }
  ```

- **`@Repository`**
  - **Rôle :** Spécialisation de `@Component`, indique que la classe est un DAO.
  - **Utilisation :** Utilisé pour marquer les classes de DAO et activer la gestion des exceptions.

- **`@Transactional`**
  - **Rôle :** Indique que les méthodes doivent être exécutées dans une transaction.
  - **Utilisation :** Utilisé pour gérer les transactions au niveau des méthodes ou des classes.

### 4. **Annotations pour la Sécurité**

- **`@Secured`**
  - **Rôle :** Indique que l'accès à une méthode est restreint aux utilisateurs avec un ou plusieurs rôles spécifiés.
  - **Utilisation :** Utilisé pour sécuriser les méthodes à un niveau granulaire.

- **`@PreAuthorize`**
  - **Rôle :** Permet des expressions de sécurité pour contrôler l'accès aux méthodes.
  - **Utilisation :** Utilisé pour des expressions de sécurité plus complexes.

  ```java
  @PreAuthorize("hasRole('ADMIN')")
  public void adminOnlyMethod() {
  }
  ```

### 5. **Annotations pour le Test**

- **`@SpringBootTest`**
  - **Rôle :** Fournit un environnement complet de Spring Boot pour les tests.
  - **Utilisation :** Utilisé pour écrire des tests d'intégration en démarrant le contexte Spring Boot complet.

- **`@DataJpaTest`**
  - **Rôle :** Configure un environnement de test pour les composants JPA.
  - **Utilisation :** Utilisé pour tester des repos JPA.

- **`@WebMvcTest`**
  - **Rôle :** Configure un environnement de test pour les contrôleurs MVC.
  - **Utilisation :** Utilisé pour tester les contrôleurs Spring MVC.

### 6. **Annotations pour les Propriétés et la Configuration**

- **`@Value`**
  - **Rôle :** Injecte des valeurs de propriété dans les champs ou les méthodes.
  - **Utilisation :** Utilisé pour injecter des propriétés de fichiers de configuration ou d'autres valeurs.

  ```java
  @Value("${app.name}")
  private String appName;
  ```

- **`@ConfigurationProperties`**
  - **Rôle :** Mappe les propriétés de configuration sur des beans.
  - **Utilisation :** Utilisé pour lire des propriétés complexes à partir de fichiers de configuration.

  ```java
  @ConfigurationProperties(prefix = "app")
  public class AppProperties {
      private String name;
      
      // getters and setters
  }
  ```

### Résumé

Les annotations Spring Boot et Spring Framework sont essentielles pour simplifier le développement en fournissant des mécanismes pour configurer, gérer et intégrer les différentes parties d'une application. En utilisant ces annotations correctement, vous pouvez tirer parti des puissantes fonctionnalités de Spring Boot pour créer des applications robustes et maintenables.
