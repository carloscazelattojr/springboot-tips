# springboot-tips
Tips for using with Spring Boot

## Application.Properties and DB Config.
- [application.properties for Spring-Boot: DB config](https://github.com/carlosjunior1983/application.properties)


## Pagination

Parâmetros de paginação
```
@RequestParam(value = "page", defaultValue = "0") Integer page,
@RequestParam(value = "linesPerPage", defaultValue = "12") Integer linesPerPage,
@RequestParam(value = "orderBy", defaultValue = "moment") String orderBy,
@RequestParam(value = "direction", defaultValue = "DESC") String direction)

```


## Tests 

<strong>@SpringBootTest</strong><br>
Carrega o contexto da aplicação (teste de integração)<br><br>

<strong>@SpringBootTest<br>
@AutoConfigureMockMvc</strong><br>
Carrega o contexto da aplicação (teste de integração & web). <br>
Trata as requisições sem subir o servidor<br><br>

<strong>@WebMvcTest(Classe.class)</strong><br>
Carrega o contexto, porém somente da camada web (teste de unidade: controlador)<br><br>

<strong>@ExtendWith(SpringExtension.class)</strong><br>
Não carrega o contexto, mas permite usar os recursos do Spring com JUnit (teste de unidade: service/component)<br><br>

<strong>@DataJpaTest</strong><br>
Carrega somente os componentes relacionados ao Spring Data JPA. Cada teste é transacional e dá rollback ao final. (teste de unidade: repository)<br><br>
