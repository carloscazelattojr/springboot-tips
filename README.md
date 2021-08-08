# springboot-tips
Tips for using with Spring Boot

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
