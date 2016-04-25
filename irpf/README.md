# Programa de Declaração do Imposto de Renda em Docker

Prepara o ambiente mínimo para a execução do IRPF da Receita Federal.

## Requisitos

Como o programa IRPF é um programa com interface gráfica, talvez seja necessário liberar acesso ao xhost

```
$ xhost -
```

Para restringir o acesso novamente, basta executar:

```
$ xhost +
```

## Executando o container

É necessário conectar o container à sua sessão do X11.

```
$ docker run -it --rm --net=host --env="DISPLAY" alisonalonso/irpf:2016
```
