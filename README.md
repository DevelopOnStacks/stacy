![Pruebas aprobadas](https://github.com/coinfabrik/stacy/actions/workflows/test.yml/badge.svg)

# STACY - Analizador Estático para Clarity en Stacks

Stacy es un analizador estático de código abierto para contratos inteligentes escritos en Clarity. Está diseñado para ayudar a los desarrolladores y auditores de contratos inteligentes en Clarity a detectar problemas comunes de seguridad y desviaciones de las mejores prácticas.

Esta herramienta ayudará a los desarrolladores a escribir contratos inteligentes más seguros y robustos.

## Instalación

```shell
pip install stacy-analyzer
```

## Documentación

- [Vulnerabilidades](https://github.com/CoinFabrik/stacy/tree/main/docs/vulnerabilities)

## Detectores

Las severidades están basadas en los peores escenarios posibles y los resultados de los detectores pueden variar según el contexto.

| ID del Detector                                                                                                                | Qué Detecta                                                                                                                                                                                               | Casos de Prueba                                                                                                                                                                                                                                          | Severidad   |
|--------------------------------------------------------------------------------------------------------------------------------| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| [assert-block-height](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/1-assert-block-height.md)             | Uso de `block-height` como rastreador de tiempo.                                                                                                                 | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/assert_block_height)                                                                                                                                                                              | Crítica     |
| [call-inside-as-contract](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/2-call-inside-as-contract.md)     | Llamar a otro contrato perdiendo el contexto del contrato inicial.                                                                                                 | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/call_inside_as_contract)                                                                                                                                                                         | Crítica     |
| [divide-before-multiply](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/3-divide-before-multiply.md)       | Realizar una operación de división antes de multiplicar, lo que provoca pérdida de precisión.                                                                      | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/divide_before_multiply)                                                                                                                                                                          | Crítica     |
| [private-function-not-used](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/4-private-function-not-used.md) | Código muerto (funciones privadas) dentro del contrato inteligente.                                                                                               | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/private_function_not_used)                                                                                                                                                                       | Mejora      |
| [todo-comment](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/5-todo-comment.md)                          | Comentarios TODO dejados en el contrato inteligente.                                                                                                              | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/todo_comment)                                                                                                                                                                                    | Mejora      |
| [tx-sender-in-assert](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/6-tx-sender-in-assert.md)             | Uso de tx-sender en assert de manera indebida.                                                                                                                     | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/tx_sender_in_assert)                                                                                                                                                                             | Alta        |
| [unwrap-panic-usage](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/7-unwrap-panic-usage.md)               | Uso inapropiado del método `unwrap-panic`, causando bloqueos inesperados en el programa.                                                                           | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/unwrap_panic_usage)                                                                                                                                                                              | Mejora      |
| [var-could-be-constant](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/8-var-could-be-constant.md)         | Variables que no cambian y podrían ser constantes.                                                                                                                | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/var_could_be_constant)                                                                                                                                                                           | Mejora      |
| [updated-functions](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/9-updated-functions.md)                 | Funciones obsoletas.                                                                                                                                               | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/updated_functions)                                                                                                                                                                               | Mejora      |
| [unused-arguments](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/10-unused-arguments.md)                  | Argumentos pasados pero no utilizados.                                                                                                                             | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/unused_arguments)                                                                                                                                                                                | Mejora      |
| [unused-let-variables](https://github.com/CoinFabrik/stacy/blob/main/docs/vulnerabilities/11-unused-let-variables.md)          | Variables locales declaradas pero no usadas.                                                                                                                       | [1](https://github.com/CoinFabrik/stacy/tree/main/tests/unused_let_variables)                                                                                                                                                                            | Mejora      |

## Directrices de Contribución

Puedes encontrar nuestras directrices de contribución [aquí](https://github.com/CoinFabrik/stacy/tree/main/docs/contribution_guidelines/contribute.md).

## Probar Stacy

Puedes ejecutar Stacy sobre todos los contratos de prueba ejecutando el siguiente comando:

```shell
stacy-analyzer lint tests
```

Buscará de forma recursiva todos los archivos `.clar` en el directorio `tests` y ejecutará Stacy sobre ellos. Con este comando, no necesitarás especificar la ruta a cada contrato inteligente.

Esto debería imprimir los errores en los ejemplos vulnerables, ¡y nada en los ejemplos corregidos!

## Acerca de CoinFabrik

Nosotros - [CoinFabrik](https://www.coinfabrik.com/) - somos una empresa de investigación y desarrollo especializada en Web3, con un sólido historial en ciberseguridad. Fundada en 2014, hemos trabajado en más de 180 proyectos relacionados con blockchain, basados en EVM y también para Solana, Algorand y Polkadot. Más allá del desarrollo, ofrecemos auditorías de seguridad a través de un equipo interno dedicado de profesionales senior en ciberseguridad, que actualmente trabaja con código en Substrate, Solidity, Clarity, Rust y TEAL.

Nuestro equipo tiene formación académica en ciencias de la computación y matemáticas, con experiencia laboral centrada en ciberseguridad y desarrollo de software, incluidas publicaciones académicas, patentes convertidas en productos y presentaciones en conferencias. Además, tenemos una colaboración continua de transferencia de conocimiento y proyectos de código abierto con la Universidad de Buenos Aires.

## Licencia

Stacy está licenciado y distribuido bajo una licencia MIT. [Contáctanos](https://www.coinfabrik.com/) si estás buscando una excepción a los términos.

