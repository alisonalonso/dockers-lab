# Programa de Declaração do Imposto de Renda em Docker

- 2019 [(2019/Dockerfile)](https://github.com/alisonalonso/dockers-lab/blob/master/irpf/2019/Dockerfile)
- 2018 [(2018/Dockerfile)](https://github.com/alisonalonso/dockers-lab/blob/master/irpf/2018/Dockerfile)
- 2017 [(2017/Dockerfile)](https://github.com/alisonalonso/dockers-lab/blob/master/irpf/2017/Dockerfile)
- 2016 [(2016/Dockerfile)](https://github.com/alisonalonso/dockers-lab/blob/master/irpf/2016/Dockerfile)
- 2015 [(2015/Dockerfile)](https://github.com/alisonalonso/dockers-lab/blob/master/irpf/2015/Dockerfile)

Prepara o ambiente mínimo para a execução do IRPF da Receita Federal.

## Requisitos

Como o programa IRPF é utiliza com interface gráfica, talvez seja necessário liberar acesso ao xhost

```
$ xhost +
```

Para restringir o acesso novamente, basta executar:

```
$ xhost -
```

## Executando o container

É necessário conectar o container à sua sessão do X11. 
Podemos realizar isto através dos argumntos `--net=host` e `--env="DISPLAY"`

```
$ docker run -it --rm --net=host --env="DISPLAY" alisonalonso/irpf
```

## Executando o Receitanet

A imagem 2016 possui o programa de transmissão Receitanet.
Para executa-lo, basta executar o container com o argumento `receitanet`

```
$ docker run -it --rm --net=host --env="DISPLAY" alisonalonso/irpf receitanet
```

## Possivel problema ao gerar a imagem

Para criar a imagem, é realizado o download dos programas IRPF e Receitanet diretamente do site da Receita.
Em algumas ocasiões, os servidores da receita não respondem, e faz-se necessário cancelar o processo e gerar novamente a imagem.
