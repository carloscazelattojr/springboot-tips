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


# Tests

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


## Fixtures 

<table>
<tbody>
<tr style="height: 23px;">
<td style="height: 23px;strong">&nbsp;JUnit 5&nbsp;</td>
<td style="height: 23px;">JUnit 4</td>
<td style="height: 23px;">Objective</td>
</tr>
<tr style="height: 23.5px;">
<td style="height: 23.5px;">&nbsp;<span style="font-weight: 400;">@BeforeAll</span></td>
<td style="height: 23.5px;">&nbsp;<span style="font-weight: 400;">@BeforeClass</span></td>
<td style="height: 23.5px;">&nbsp;<span style="font-weight: 400;">Prepara&ccedil;&atilde;o antes de todos testes da classe (m&eacute;todo est&aacute;tico)</span></td>
</tr>
<tr style="height: 23px;">
<td style="height: 23px;">&nbsp;<span style="font-weight: 400;">@AfterAll</span></td>
<td style="height: 23px;">&nbsp;<span style="font-weight: 400;">@AfterClass</span></td>
<td style="height: 23px;">&nbsp;<span style="font-weight: 400;">Prepara&ccedil;&atilde;o depois de todos testes da classe (m&eacute;todo est&aacute;tico)</span></td>
</tr>
<tr style="height: 23px;">
<td style="height: 23px;">&nbsp;<span style="font-weight: 400;">@BeforeEach</span></td>
<td style="height: 23px;">&nbsp;<span style="font-weight: 400;">@Before</span></td>
<td style="height: 23px;">&nbsp;<span style="font-weight: 400;">Prepara&ccedil;&atilde;o antes de cada teste da classe </span></td>
</tr>
<tr style="height: 23px;">
<td style="height: 23px;">&nbsp;<span style="font-weight: 400;">@AfterEach</span></td>
<td style="height: 23px;">&nbsp;<span style="font-weight: 400;">@After</span></td>
<td style="height: 23px;">&nbsp;<span style="font-weight: 400;">Prepara&ccedil;&atilde;o depois de cada teste da classe </span></td>
</tr>
</tbody>
</table>

## Mockito vs @MockBean
<table>
<tbody>
<tr>
<td>&nbsp;
<p><span style="font-weight: 400;">@Mock</span></p>
<p><span style="font-weight: 400;">private MyComp myComp;</span></p>
<p><span style="font-weight: 400;">ou&nbsp;</span></p>
<p><span style="font-weight: 400;">myComp = Mockito.mock(MyComp.class)</span></p>
</td>
<td>&nbsp;
<p><span style="font-weight: 400;">Usar quando a classe de teste n&atilde;o carrega o contexto da aplica&ccedil;&atilde;o. &Eacute; mais r&aacute;pido e enxuto.</span></p>
<p><span style="font-weight: 400;">@ExtendWith</span></p>
</td>
</tr>
<tr>
<td>&nbsp;
<p><span style="font-weight: 400;">@MockBean</span></p>
<p><span style="font-weight: 400;">private MyComp myComp;</span></p>
</td>
<td>&nbsp;
<p><span style="font-weight: 400;">Usar quando a classe de teste carrega o contexto da aplica&ccedil;&atilde;o e precisa mockar algum bean do sistema.</span></p>
<p><span style="font-weight: 400;">@WebMvcTest</span></p>
<p><span style="font-weight: 400;">@SpringBootTest</span></p>
</td>
</tr>
</tbody>
</table>

<br>
<hr>
<br>

# POSTMAN 

#### Configurar variavel de Environment {{token}}

Crie um environment.
crie uma variável token.
Na sua requisição de login /oauth/, na aba tests coloque o script abaixo.

```
if (responseCode.code >= 200 && responseCode.code < 300) {
    var json = JSON.parse(responseBody);
    postman.setEnvironmentVariable('token', json.access_token);
}
```
![Image](https://github.com/carlosjunior1983/springboot-tips/blob/main/postman1.JPG "Environment")

![Image](https://github.com/carlosjunior1983/springboot-tips/blob/main/postman2.JPG "Environment")




