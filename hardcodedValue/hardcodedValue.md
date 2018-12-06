## Introduction (problématique)
Avez vous déjà rencontré un warning de sonar qui vous dit hey " VARIABLE should not be hardcoded"
c'est le cas d'éviter ce problème. (c'est juste une introdution pour monter l'interêt de cet outil  👍).

La régle générale : [URIs should not be hardcoded](https://rules.sonarsource.com/java/RSPEC-1075)
code smell
## Exemple
Supposons que vous avez un fichier et vous cherchez à  le lire (parser), donc vous êtres obligés de passer son chemin comme paramètre .
pour ce faire il y a plusieurs façons.
### Première 
Vous le passez en dure "le chemin tel quel est"  "C:\\Program Files\\folder\\file.txt"
```java 
	public class FileParser{
        public void readFile() throws FileNotFoundException{
        	BufferedReader br = new BufferedReader(new FileReader("C:\\Program Files\\folder\\file.txt"));
             
        }

}
```
### Deuxième 
Peut-être définir le chemin comme une constante mais ça reste toujours à l'intérieur de notre classe.
```java 
     public class FileParser{
	static final String FILEPATH="C:\\Program Files\\folder\\file.txt";
        public void readFile() throws FileNotFoundException{
        	BufferedReader br = new BufferedReader(new FileReader(FILEPATH));
             
        }

}
```
### Troisième  
C'est le fait de définir un fichier externe qui contient généralement tous les valeurs constantes, qui seront utilisées à l'intérieur de votre code.la chose qui vous permet en cas de changement de certaines valeurs de les  modifier une seule fois dans le fichier de configuration (fichier externe).
dans cet exemple je vais stocker les valeurs dans le fichier application.properties du projet spring boot .

1. définir la valeur dans le fichier de configuration (application.properties)
```text
file.path=C:\\Program Files\\folder\\file.txt

```

2. déclarer la valeur dans la classe réceptrice de de la valeur
```java
	@Value("${file.path}")
	private String filePath;
```

3. passer la valeur aux méthodes en question

```java 
     public class FileParser{
        @Value("${file.path}")
	private String filePath;
        public void readFile() throws FileNotFoundException{
        	BufferedReader br = new BufferedReader(new FileReader(filePath));
             
        }

}
```
### Quatrième  
Définir une classe pour faire le mapping entre le fichier application.properties(example), géréralement un fichier dédié au configuration.
1. définir le fichier de configuration.
```file 
user.name=anass
user.email=email@email.com
```
2. déclaration de la classe de configuration avec l'ajout de certainnes annotations.
```java
@Configuration
@ConfigurationProperties(prefix="user")
public class User {
	private String name;
	private String email;
	// getters et setters
```
3. utilisation de la configuration
```java
  @RestController
  public class UserController {
	@Autowired
	User user;

	@GetMapping("/users")
	User getUser() {
		User storeUser = new User();
		storeUser.setName(user.getName());
		storeUser.setEmail(user.getEmail());
		return storeUser;
		}

	}
```
Brief l'externalisation des valeurs reste valable pour plusieurs cas (URL,chemin de fichier, configuration de base de données,données par defaut, ......) .

Pour plus de détails sur les règles de contrôle de qualité de code n'hésitez pas à visiter ce lien.[sonarsource](https://rules.sonarsource.com/java/RSPEC-1075)
