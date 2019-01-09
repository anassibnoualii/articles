## Introduction 
Le swagger est une documentation  qui spécifie généralement l'utilisation d'une API. Donc son interêt est décrire l'ensemble des
fonctionnalités fournises par une API. C'est-à-dire  comment exploiter les ressources exposées par l'API.
## Dependency
On ajoute dans le fichier pom.xml du projet maven les dépendances suivantes.
``` 
		<dependency>
			<groupId>io.springfox</groupId>
			<artifactId>springfox-swagger2</artifactId>
			<version>2.7.0</version>
		</dependency>
		<dependency>
			<groupId>io.springfox</groupId>
			<artifactId>springfox-swagger-ui</artifactId>
			<version>2.7.0</version>
		</dependency>
```
## Configuration

1. créer une classe de configuration qui contient les annotations suivantes : 
```java
@Configuration
@EnableSwagger2
```
Comme suit: 
```java
@Configuration
@EnableSwagger2
public class SwaggerConfig {
	@Bean
	public Docket api() {
		return new Docket(DocumentationType.SWAGGER_2).select()
				.apis(RequestHandlerSelectors.basePackage("springbootApi")).paths(PathSelectors.any()).build()
				.apiInfo(apiInfo());
	}

	private ApiInfo apiInfo() {
		return new ApiInfo("My REST API", "Some custom description of API.", "API TOS", "Terms of service",
				new Contact("Anass IBNOU ALI", "https://github.com/anassibnoualii", "annass.ibnouali@gmail.com"), "License of API",
				"API license URL", Collections.emptyList());
	}

}
```
2. Implimenter les beans et  méthodes que vous avez besoin : 
La bean Api vouspermet de spécifier le package qui sera scanner et qui contient vous ressources à exposer généralement les controllers (@RestController). Ainsi de definir plusieurs méthodes comme ApiInfo qui vous présente des informations générale sur Api. Il est possible aussi d'ajouter des restrictions sur des chemins, de personnaliser les codes de retour http  ....
## Annotation utiles
Pour faciliter la documentations plusieurs annotations sont fournies.
1.Annotation pour les classes (controller) : 
```java
        @Api(value="users", description="get and post users ")
        public class UserController {
        }
```
2.Annotations sur les  méthodes : 
```java
        @ApiOperation(value = "View a list of users)
        @GetMapping("/users")	public List<User> findAll() {
		return userRepository.findAll();
	}
```
3. Annotations pour les codes de retour http : 
```java
       @ApiResponses(value = {
       @ApiResponse(code = 200, message = "Successfully retrieved list"),
       @ApiResponse(code = 401, message = "You are not authorized to view the resource"),
       @ApiResponse(code = 403, message = "Accessing the resource you were trying to reach is forbidden"),
       @ApiResponse(code = 404, message = "The resource you were trying to reach is not found")})
```
