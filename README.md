<h1 style='color: #DAA520; font-size: 34px; font-weight: bold;'>Análise e Previsão de Aluguel de Imóveis em São Paulo</h1>

# <font color="black" style="font-size: 30px;">Objetivo</font>

<p style='font-size: 23px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;'>    
<i><b> Construir uma análise abrangente do mercado imobiliário de aluguel em São Paulo, Brasil, utilizando técnicas de ciência de dados. O projeto incluirá exploração de dados, visualizações informativas e construção de um modelo de previsão de aluguel com base nas características dos imóveis</b></i>     
</p>

---

<p style=' font-size: 30px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;text-indent: 0px; color: #DC143C;'>    
<i><b> Informações do Dataset (distribuição, frequência, Estatísticas Descritivas, etc) </b></i>     
</p>

---

### - Verifiquei num primeiro momento caracteristicas gerais da minha base de dados, como tipo das colunas, numéro de elementos naõ nulos e também o tamanho dessa base.

### - Visualizei como os imóveis se distribuiam dentro da amostragem tanto por endereço quando por distrito. O objetivo era conhecer as regiões de São Paulo que temos mais informações. Segue os gráficos abaixo:

![image](https://github.com/MiguelFreire-bit/Aluguel_Imoveis-SP-ProjetoDS/assets/72529654/59c70260-585f-408a-8b07-b2f113a50547)

---

![image](https://github.com/MiguelFreire-bit/Aluguel_Imoveis-SP-ProjetoDS/assets/72529654/e1bfa2e1-ed94-47e5-9d35-863da0c27898)

### Também é interessante conhecer quais são os tipos de imóveis que temos nos dados e como estão distribuídos.

![image](https://github.com/MiguelFreire-bit/Aluguel_Imoveis-SP-ProjetoDS/assets/72529654/89329724-0e89-4fb9-8904-d9cb76249934)





---

<p style=' font-size: 30px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;text-indent: 0px; color: #DC143C;'>    
<i><b>Relações entre as variáveis (correlação, gráfico de dispersão e heatmap)</b></i>     
</p>

---

### Percebe-se uma relação altíssima entre as variáveis numéricas, o que é positivo, porém também pode ser desvantajoso, pois pode resultar em multicolinearidade em um modelo

![image](https://github.com/MiguelFreire-bit/Aluguel_Imoveis-SP-ProjetoDS/assets/72529654/c31864da-3444-4c01-b6a5-2118423c7bd6)

### vamos observar, por exemplo, a relação de Area e Aluguel:

![image](https://github.com/MiguelFreire-bit/Aluguel_Imoveis-SP-ProjetoDS/assets/72529654/d0bce17d-9624-4308-b574-765966a12861)

<p style='font-size: 23px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;'>    
<i><b>Algumas observações:

### 1 - Percebe-se claramente um outlier de um imóvel com valor de aluguel de 25 mil reais, muito fora do padrão dos dados. Acrescenta-se ainda que a área desse imóvel é pequena, o que causa estranheza.



### 2 - Também se percebe um padrão estranho nos aluguéis de 15 mil reais. Praticamente uma linha, simbolizando que há imóveis de quase todos os tamanhos custando esse valor.

### 3 - Imóveis de baixo custo, mas com áreas grandes: Será que se encontram em bairros mais periféricos, mais desvalorizados? Qual a média do preço de aluguéis nesses locais? É realmente o preço padrão dessas localidades ou esses imóveis são outliers?

</b></i>     

</p>

---

<p style=' font-size: 25px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;text-indent: 0px; color: #DC143C;'>    
<i><b>VERIFICANDO MULTICOLINEARIEDADE USANDO VIF</b></i>     
</p>

---

<p style='font-size: 23px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;'>    
<i><b>

### O VIF é uma medida estatística que indica a extensão da multicolinearidade entre as variáveis independentes em um modelo de regressão. Ele quantifica quanto a variância de um coeficiente de regressão está aumentada devido à multicolinearidade. Valores de VIF maiores do que 10 são geralmente considerados preocupantes e indicam uma multicolinearidade significativa.

</b></i>     

</p>

<p style='font-size: 23px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;'>    
<i><b>

### - Os valores de VIF que obtive indicam que não há uma multicolinearidade significativa entre as variáveis independentes para um modelo, o que é uma boa notícia para a validade dos resultados de regressão.

### - A importância de toda essa análise estatística inicial é compreender se os dados disponíveis ja estão bem ajustados, inicialmente.

</b></i>     

</p>

---

<p style=' font-size: 25px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;text-indent: 0px; color: #DC143C;'>    
<i><b>Primeiros passos para definir modelo de previsão de preço</b></i>     
</p>

---

### Verificar as métricas do modelo para distritos com diferentes quantidades de imóveis.

### MSE por Distrito

![image](https://github.com/MiguelFreire-bit/Aluguel_Imoveis-SP-ProjetoDS/assets/72529654/de3cd038-cd48-48e5-9cdb-653961eb393f)

---

R² por distrito

![image](https://github.com/MiguelFreire-bit/Aluguel_Imoveis-SP-ProjetoDS/assets/72529654/9f944248-47f3-461d-9499-22076683ba25)

---

<p style='font-size: 23px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;'>    
<i><b>

## 1. MSE (Erro Quadrático Médio):

---

### - Quanto menor o valor do MSE, melhor é o desempenho do modelo. Ele mede a média dos quadrados dos erros, ou seja, quanto mais próximo de zero, melhor é a capacidade do modelo em prever os valores reais.

<hr style="border: 2px solid green;">

## 2. R² (Coeficiente de Determinação):

---    

### - O R² varia de 0 a 1 e representa a proporção da variância na variável dependente que é previsível a partir das variáveis independentes.

### - Um valor próximo de 1 indica que o modelo é capaz de explicar uma grande parte da variabilidade dos dados.

### - Um valor próximo de 0 indica que o modelo não consegue explicar a variabilidade dos dados.

### - Valores negativos indicam que o modelo é pior do que uma simples média dos dados.



<hr style="border: 2px solid green;">

## 3. Resultado do Modelo de Teste

---

### - Observando nossos dados podemos perceber que de 300 a 50 amostras o desempenho do modelo é bom e estável (MSE baixa e R² alto)

### - Porém, abaixo de 50 começamos a ter quedas bruscas nas métricas do modelo

<hr style="border: 2px solid green;">

# Portanto:

### - Irei utilizar os distritos com no mínimo 50 imóveis

---

<p style=' font-size: 25px; line-height: 2; margin-top: 20px; margin: 0px 0px; text-align: justify; text-indent: 0px;text-indent: 0px; color: #DC143C;'>    
<i><b>Modelo de Previsão do preço dos alugueis</b></i>     
</p>

---



```python

# Função para prever o preço do aluguel com base no tipo e distrito
def prever_preco(distrito, tipo):
    try:
        df_modelo = df[df['district'] == distrito]
        df_modelo_numerico = df_modelo.select_dtypes(include='number')


        X = df_modelo_numerico.drop('rent', axis=1)
        y = df_modelo_numerico['rent']

        # Dividir o conjunto de dados em treino e teste
        X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

        # Criar e treinar o modelo de Random Forest
        modelo = RandomForestRegressor(n_estimators=100)
        modelo.fit(X_train, y_train)  

        # Escolhendo o tipo 
        df_modelo = df_modelo[df_modelo['type'].isin([tipo])]
        dados = df_modelo.select_dtypes(include='number').drop('rent', axis=1)

        # Fazer previsões no conjunto de teste
        predicao = modelo.predict(dados)    

        return print(f"Preço médio de aluguel nesse distrito para {tipo} é : R$ {round(predicao.mean(),2)}")

    except:
        if len(dados) == 0:
            print(f"Não há imóveis do tipo '{tipo}' em {distrito}")


```



---

<p style=' font-size: 25px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;text-indent: 0px; color: #DC143C;'>    
<i><b>Interface gráfica para interação do usuário com o modelo</b></i>     
</p>

---



```python
# Opções para distrito e tipos

distritos = sorted(distritos_aptos) #lista com os distritos
type_ = sorted(df.type.unique()) #lista com os tipo de imóvel


# Widgets para seleção de tipo e distrito

distrito_widget = widgets.Dropdown(options=distritos ) # os widgets Dropdown são menus suspensos 
types_widget = widgets.Dropdown(options=type_) # os widgets Dropdown são menus suspensos 


# Layout de caixa para adicionar um título
titulo_distrito = widgets.Label(value="Selecione o Distrito:") # título que vem a esquerda do menu suspenso
box_distrito = widgets.Box([titulo_distrito, distrito_widget]) # caixa compreende o titulo e o widget

titulo_tipo = widgets.Label(value="Selecione o Tipo de Imóvel:")# título que vem a esquerda do menu suspenso
box_tipo = widgets.Box([titulo_tipo, types_widget]) # caixa compreende o titulo e o widget

# Título da interface
titulo_interface = widgets.HTML("<h3 style='text-align:left'>PREÇO DE ALUGUEL</h3>") # título

# Botão para fazer a previsão
botao_prever = widgets.Button(description='Prever', style={'button_color': 'lightgreen', 'position': 'right'}) #botão

# Função para lidar com o evento de clique no botão
def on_prever_clicked(b):

    preco_previsto = prever_preco(distrito_widget.value, types_widget.value)


# Associar a função de clique do botão ao evento de clique
botao_prever.on_click(on_prever_clicked)

# Exibir widgets
widgets.VBox([titulo_interface, box_distrito, box_tipo, botao_prever, ])
```





---

<p style=' font-size: 25px; line-height: 2; margin: 0px 0px; text-align: justify; text-indent: 0px;text-indent: 0px; color: #DC143C;'>    
<i><b>Exemplo de aplicação</b></i>     
</p>

---



**Painel interativo**

![9e69336d-96f1-4501-8dfb-f276ce7e13df](file:///C:/Users/Migue/OneDrive/Imagens/Typedown/9e69336d-96f1-4501-8dfb-f276ce7e13df.png)



**Resposta**

![29733bef-8752-4b7e-bff7-706efd5b4322](file:///C:/Users/Migue/OneDrive/Imagens/Typedown/29733bef-8752-4b7e-bff7-706efd5b4322.png)

---



Se tiver alguma dúvida ou sugestão, sinta-se à vontade para entrar em contato:

* E-mail: [miguelsilvafreire@hotmail.com](mailto:seuemail@example.com)
* LinkedIn: [www.linkedin.com/in/miguel-freire99/](https://www.linkedin.com/in/seuperfil/)

Contribuições e feedback são sempre bem-vindos!


