# Estágio 1: Build da aplicação com Maven
# Usamos uma imagem que já contém o JDK e o Maven
FROM maven:3.9.6-eclipse-temurin-21 AS build

# Define o diretório de trabalho dentro do container
WORKDIR /app

# Copia o arquivo pom.xml para que o Docker possa cachear as dependências
COPY pom.xml .

# A linha 'COPY .mvn .mvn' foi removida para evitar o erro "not found"

# Baixa as dependências do projeto
# O 'dependency:go-offline' é bom para forçar o download e usar o cache.
RUN mvn dependency:go-offline

# Copia o restante do código fonte (incluindo a pasta 'src')
COPY src ./src

# Executa o build do projeto, gerando o arquivo .jar
# -DskipTests para pular a execução dos testes
RUN mvn package -DskipTests

# Estágio 2: Criação da imagem final (Runtime)
# Usamos uma imagem mais leve, contendo apenas o JRE, para rodar a aplicação
FROM eclipse-temurin:21-jre-jammy

# Define o diretório de trabalho
WORKDIR /app

# Copia o arquivo .jar gerado no estágio de build para a imagem final
# O '*' garante que o Docker encontre o nome exato do JAR (ex: bibliotecajogos-0.0.1-SNAPSHOT.jar)
COPY --from=build /app/target/*.jar app.jar

# Expõe a porta que a aplicação Spring Boot usa por padrão
EXPOSE 8080

# Comando para iniciar a aplicação quando o container for executado
# Este é o comando de 'Start' (java -jar target/*.jar) no seu guia
ENTRYPOINT ["java", "-jar", "app.jar"]