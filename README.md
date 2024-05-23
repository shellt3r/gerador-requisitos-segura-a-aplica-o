# Sobre
Gerador de requisitos de segurança de aplicativos, baseado em ASVS, guia de testes OWASP e alguma experiência :)

![Tela inicial do aplicativo](/images/requirements.png?raw=true "Tela inicial do aplicativo")

## Mais sobre o problema
Muitos de vocês viram um enorme conjunto de requisitos do OWASP e encontraram desenvolvedores com muitas palavras sobre um documento tão grande.
Caso contrário, você pode encontrá-lo [aqui](https://owasp.org/www-pdf-archive/OWASP_Application_Security_Verification_Standard_4.0-en.pdf) e tentar compartilhá-lo com os desenvolvedores sem prepará-los :)

## O que fizemos
- Dividir os requisitos ASVS por funcionalidade
- Adicionada uma função para marcar alguns requisitos como importantes (para que seus desenvolvedores possam começar a partir deles, por exemplo)
- Mapeamento de requisitos para testes
- Compartilhei para você neste repositório e [em nosso subdomínio](https://requirements.whitespots.io/en)

## Agora você pode
- Use nossa ferramenta gratuita online [aqui](https://requirements.whitespots.io/en)
- Utilize nossa ferramenta gratuita em sua infraestrutura (veja instruções abaixo)

E tenha um conjunto útil de requisitos **importantes** e **relevantes**:

![pdf](/images/pdf_download.png?raw=true "pdf")

# Clone
```bash
clone git https://github.com/Whitespots-OU/security-requirements-generator.git srg && \
cd srg
```

# Implantar
## Servidor
```bash
exportar BASE_URL=http://hostname.com
docker-compose up -d --build
docker-compose run back migrar
docker-compose executar back loaddata
docker-compose executar de volta collectstatic
docker-compose exec back ./manage.py create_super_user --username admin --password SENHA
abra https://hostname.com/admin/ # para fazer login e definir o nome da sua empresa
```

## Local
### Voltar
- criar virtualenv e instalar requisitos
```bash
cd de volta
pyenv virtualenv 3.9.0 srg_back
pyenv ativar srg_back
pip instalar poesia
instalação de poesia
```
- definir ambientes
```bash
exportar DEBUG = ativado
exportar ALLOWED_HOSTS=*
exportar BASE_URL=http://localhost:8000
exportar REDIS_DSN=redis://localhost:6379/0
exportar DB_USER = usuário
exportar DB_PASS = senha
exportar DB_HOST=localhost
exportar DB_NAME=srg
```
- chame `pre-commit install` na linha de comando
- criar banco de dados no mercado pg
- adicionar ambientes de [.env.dev](back/.env.dev)
- aplicar migrações de banco de dados `./manage.py migrate`
- criar superusuário `./manage.py create_super_user`
- execute servidor local `./manage.py runserver`
- abra o [painel de administração](http://localhost:8000/admin/) e faça login como admin:admin
- chame `make pre-commit` antes de fazer um commit

### Frente
```bash
frente do CD
instalação npm
npm executar servir
abra http://localhost:8080
npm executar compilação
```

# PERGUNTAS FREQUENTES
### Como adicionar minhas próprias categorias (funções do aplicativo), requisitos e testes?
1. Basta visitar <your_host>/admin e fazer login no administrador do Django 
2. Vá para categorias/requisitos/testes (depende do que você deseja adicionar/editar)
3. Depois disso, execute `docker-compose run back dumpdata`
Ele fará um despejo de todas as suas categorias, requisitos e configurações de testes atuais

### Como contribuir com categorias, requisitos, testes?
Isto não cobrirá TODOS os requisitos possíveis, descritos na íntegra no OWASP ASVS.
Em vez disso, esta ferramenta foi projetada para ajudar pequenas equipes a acompanhar as coisas mais importantes e relevantes.

1. Antes de adicionar algo novo, tente encontrar o mesmo requisito/teste/categoria nos dados existentes
2. Sinta-se à vontade para descrever melhor os testes/requisitos existentes
3. Descreva suas alterações na solicitação de mesclagem 
- Coloque suas alterações em um título: Nova categoria/Novos requisitos/Novos testes 
- Descrever no texto quais problemas foram resolvidos e quais não foram 

# Colaboradores

## Desenvolvimento
@alex-deus - Fiz todos esses repositórios legais com código funcional

## Motivadores de ideias
- @sarosbacz - Percebi que requisitos se misturam com testes sem categorias
- @httpnotonly - Reuniu todos

## Agradecimentos especiais por trabalhar com conteúdo
- @totoshky - Redução de complexidade e refatoração de acordo com tendências recentes de segurança
- @edgesec
- @W0uldYk1ndlY

## Hackers
- @shellt3r - Testou e traduziu os documentos para pt_BR
- @acrono - Nos deu mais requisitos e testes
- @a_ashwarya - Nos deu mais requisitos e testes
