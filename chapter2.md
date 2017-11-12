---
title       : Obtenção dos dados
description : Aqui você exercitará a importação do dataset que utilizaremos no nosso estudo de caso 
attachments :
slides_link : 

---
## More movies

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: 6951acb932
```

Vamos importar o arquivo que será utilizado para a análise de evasão de colaboradores 

O arquivo `dadosEvasao.csv` est'á dispon'ível no seu workspace. Basta importá-lo utilizando o comando de importação do R

`@instructions`
- Importe o arquivo `dadosEvasao.csv`.
- Analise os dados importados utilizando os comandos `head(<nome_do_dataframe>)` e `tail(<nome_do_dataframe>)`

`@hint`
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

`@pre_exercise_code`
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
load(url("https://s3.amazonaws.com/assets.datacamp.com/course/teach/movies.RData"))
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"), c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

`@sample_code`
```{r}
# Importe o arquivo de dados de evasão de colaboradores. Ele está carregado no ambiente com o nome "dadosEvasao.csv"
dadosEvasao <- _______.______(________)

# Confira a importa'ç˜ção utilizando os comandos head() e tail()

```

`@solution`
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

`@sct`
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_movies")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()

success_msg("Good work!")
```
