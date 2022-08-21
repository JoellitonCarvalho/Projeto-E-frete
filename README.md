Aplicativo de exemplo do Android para buscar o repositório do Github 




1. Este projeto consiste em vários módulos
2. Módulo de recursos dinâmicos. (repositório de detalhes)
3. Padrão de design MVVM




## Requerimento:                                                                                       

Aplicativo que mostra os 50 principais repositórios github mais estrelados pesquisando com
a palavra-chave "Android".

Uma página de lista de repositórios onde a lista de repositórios era exibida. 
 Lista obtida em https://api.github.com/ api usando "Android" como palavra-chave de consulta. 
 A lista pode ser classificada por data e hora da última atualização ou contagem de estrelas. 
 A opção de classificação selecionada persiste em outras sessões do aplicativo. 
 Uma página de detalhes do repositório, para a qual navegou clicando em um item da lista. 
 A página de detalhes mostra o nome do proprietário do repositório, foto, descrição do repositório, data da última atualização.
 Hora no formato mês-dia-ano hora: segundos, cada campo em números de 2 dígitos. Concluído (tenho um problema com o dispositivo abaixo do Android 8)
 O repositório que carregou uma vez é salvo para navegação offline.                                








## Bibliotecas utilizadas:          
 Jetpack Compose         
 Navigation              
 View Binding            
 ViewModel               
 LiveData                 
 Kotlin Coroutine        
 Dagger2                 
 Hilt                    
 Room Database           
 Retrofit                


 


## Build HTTP Client
Retrofit.Builder()
      .client(okHttpClient)
      .baseUrl("https://api.github.com/")
      .addConverterFactory(converterFactory)
      .build()

## Build Request  APi
  interface Service {
    @GET("search/repositories")
    suspend fun getHotRepos(
      @Query("q") query: String="Android",
      @Query("sort") sort: String = "stars",
      @Query("order") order: String = "desc",
      @Query("page") page: Int = 1,
      @Query("per_page") per_page: Int = 50
    ): ListResponse<RepositoryResponse>

  }

#Feature 

1. Mostrar lista de repositórios do github
2. Mostrar detalhes para cada repositório 
3. O repositório pode ser ordenado por contagem de estrelas ou atualizado pela última vez 
4. O pedido selecionado será salvo para futuro 
5. Salvar dados de navegação
6. Excluir dados de navegação ao pressionar longamente

