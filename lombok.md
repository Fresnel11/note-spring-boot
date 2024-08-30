Lombok est une bibliothèque Java qui simplifie le code en générant automatiquement du code boilerplate, tel que les getters, setters, constructeurs, et plus encore. Cela permet aux développeurs de se concentrer sur la logique métier plutôt que sur le code répétitif.

### Installation

Pour utiliser Lombok dans un projet Maven, ajoutez la dépendance suivante dans votre fichier `pom.xml` :

```xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.26</version> <!-- Vérifiez la dernière version disponible -->
    <scope>provided</scope>
</dependency>
```

Pour Gradle, ajoutez cette ligne dans votre fichier `build.gradle` :

```groovy
dependencies {
    compileOnly 'org.projectlombok:lombok:1.18.26' // Vérifiez la dernière version disponible
    annotationProcessor 'org.projectlombok:lombok:1.18.26'
}
```

### Principales Annotations de Lombok

Voici un aperçu des annotations les plus couramment utilisées avec Lombok :

#### 1. **@Getter et @Setter**

- **@Getter** : Génère automatiquement les méthodes getter pour tous les champs de la classe.
- **@Setter** : Génère automatiquement les méthodes setter pour tous les champs de la classe.

**Exemple :**

```java
import lombok.Getter;
import lombok.Setter;

@Getter
@Setter
public class Person {
    private String name;
    private int age;
}
```

Cela génère les méthodes `getName()`, `setName(String name)`, `getAge()`, et `setAge(int age)` automatiquement.

#### 2. **@ToString**

- **@ToString** : Génère automatiquement une méthode `toString()` qui affiche les valeurs des champs de la classe.

**Exemple :**

```java
import lombok.ToString;

@ToString
public class Person {
    private String name;
    private int age;
}
```

Cela génère une méthode `toString()` qui retourne une chaîne avec le nom de la classe et les valeurs des champs.

#### 3. **@EqualsAndHashCode**

- **@EqualsAndHashCode** : Génère automatiquement les méthodes `equals(Object o)` et `hashCode()` basées sur les champs de la classe.

**Exemple :**

```java
import lombok.EqualsAndHashCode;

@EqualsAndHashCode
public class Person {
    private String name;
    private int age;
}
```

#### 4. **@NoArgsConstructor, @AllArgsConstructor, @RequiredArgsConstructor**

- **@NoArgsConstructor** : Génère un constructeur sans arguments.
- **@AllArgsConstructor** : Génère un constructeur avec tous les arguments pour les champs.
- **@RequiredArgsConstructor** : Génère un constructeur avec les arguments pour les champs `final` et les champs marqués avec `@NonNull`.

**Exemple :**

```java
import lombok.NoArgsConstructor;
import lombok.AllArgsConstructor;
import lombok.RequiredArgsConstructor;

@NoArgsConstructor
@AllArgsConstructor
@RequiredArgsConstructor
public class Person {
    private String name;
    private int age;
    private final String id; // Utilisé par @RequiredArgsConstructor
}
```

#### 5. **@Data**

- **@Data** : Une annotation combinée qui inclut `@Getter`, `@Setter`, `@ToString`, `@EqualsAndHashCode`, et un constructeur pour les champs `final` (si présents).

**Exemple :**

```java
import lombok.Data;

@Data
public class Person {
    private String name;
    private int age;
}
```

#### 6. **@Builder**

- **@Builder** : Génère un constructeur fluent pour créer des instances de la classe en utilisant un modèle de constructeur basé sur le style "builder".

**Exemple :**

```java
import lombok.Builder;
import lombok.ToString;

@Builder
@ToString
public class Person {
    private String name;
    private int age;
}
```

Avec `@Builder`, vous pouvez créer une instance de `Person` comme suit :

```java
Person person = Person.builder()
                      .name("John Doe")
                      .age(30)
                      .build();
```

#### 7. **@Slf4j, @Log, @Log4j, @Log4j2, @CommonsLog, @XSlf4j**

- **@Slf4j** : Génère un logger SLF4J pour la classe.
- **@Log** : Génère un logger Java Util Logging.
- **@Log4j** : Génère un logger Log4j.
- **@Log4j2** : Génère un logger Log4j2.
- **@CommonsLog** : Génère un logger Apache Commons Logging.
- **@XSlf4j** : Génère un logger XSLF4J.

**Exemple :**

```java
import lombok.extern.slf4j.Slf4j;

@Slf4j
public class MyService {
    public void doSomething() {
        log.info("Doing something...");
    }
}
```

### Conclusion

Lombok est un outil puissant qui réduit le boilerplate code en Java, ce qui rend votre code plus lisible et plus facile à maintenir. En utilisant les annotations de Lombok, vous pouvez générer automatiquement des méthodes courantes et des constructeurs, ce qui simplifie le processus de développement et améliore la qualité du code.
