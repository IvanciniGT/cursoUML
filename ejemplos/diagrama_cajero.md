
# Diagrama de secuencia para sacar dinero en un cajero automático

## HAPPY PATH: Es el camino feliz.-.. SI TODO VA COMO DEBERIA... Super bien!


```mermaid

sequenceDiagram

    actor                   U as Usuario
    participant             C as Cajero
    participant             S as Servidor

    U->>C:                  💳 Insertar tarjeta
    C->>U:                  Solicitar PIN
    U->>C:                  Escribe su PIN
    C->>+S:                 Solicitar validación del PIN de la tarjeta
    S-->>C:                 PIN correcto
    C->>U:                  Solicitar cantidad
    U->>C:                  Escribe la cantidad
    C->>S:                  Retirar importe solicitado
    S-->>C:                 OK
    C-->>U:                 💳 Entrega la tarjeta
    C-->>U:                 💰 Entrega el dinero

```

Una vez montado este, identificamos los posibles problemas y los tratamos en el diagrama de secuencia.


## FLUJO COMPLETO Y ARCHIDETALLADO

```mermaid

sequenceDiagram

    actor                   U as Usuario
    participant             C as Cajero
    participant             S as Servidor

    U->>C:                  💳 Insertar tarjeta

    rect rgb(255,240,230)
        note left of C:                 LECTURA DE LA TARJETA
        critical                        Leer tarjeta
        option                          Tarjeta caducada
            rect rgb(255,230,200)
                break                   No se puede procesar la operación
                    C-->>U:                 Tarjeta caducada
                    C-->>U:                 💳 Entrega la tarjeta
                end
            end
        option                          Error al leer la tarjeta
            rect rgb(255,230,230)
                break               
                    C-->>U:                 Tarjeta no legible
                    C-->>U:                 💳 Entrega la tarjeta
                end
            end
        end
    end
    rect rgb(255,255,230)
        note left of S:                 PIN
        loop                            Hasta 3 intentos si el pin no es válido
            rect rgb(235,235,200)
                note left of C:         Obtención del PIN
                C-->>U:                 Solicitar PIN
                critical                Esperar el PIN
                    U->>C:                  Escribe su PIN
                option                  No se ha introducido el PIN en 30 segundos
                    rect rgb(255,230,230)
                        break
                            C->>U:          No se puede procesar la operación
                            C->>U:          💳 Entrega la tarjeta
                        end
                    end
                end
            end 
            rect rgb(235,235,180)
                note left of S:         Validación del PIN
                C->>+S:                 Solicitar validación del PIN de la tarjeta
                critical                Validar PIN
                        S-->>C:         PIN correcto
                option                  PIN incorrecto
                        S-->>C:         PIN incorrecto
                option                  Servidor con problemas internos
                    S-->>-C:             Notifica problemas internos
                option                  Timeout
                    note left of S:     El servidor no contesta
                end

                opt                     Si ha habido timeout o problemas internos
            rect rgb(255,230,230)
                    break               No se puede validar el PIN
                        C-->>U:         💳 Entrega la tarjeta
                        C-->>U:         No se puede procesar la operación
                    end
                    end
                end
            end 
        end

            rect rgb(235,235,180)
        critical                Si no se ha conseguido un PIN correcto
            rect rgb(255,230,230)
                    break               
                        C-->>U:         💳 Entrega la tarjeta
                        C-->>U:         No se puede procesar la operación
                    end
                end
            end
            end
    end 

    rect rgb(240,240,255)
        note left of S:     SACAR DINERO

        loop Hasta 3 intentos si la cantidad no es válida
            rect rgb(230,230,255)
                note left of C:         Cantidad
                C-->>U:                 Solicitar cantidad
                critical                     Esperar la cantidad la Cantidad
                    U->>C:                  Escribe la cantidad
                    opt                 Si no hay suficiente dinero o <BR/>no se le puede entregar
                        C-->>U:         No hay tanto dinero o <BR/>debe introducir una cantidad <BR/>múltiplo del tipo de<BR/> billetes disponibles
                    end
                option                 No se ha introducido la cantidad en 30 segundos
            rect rgb(255,230,230)
                        break                 
                            C->>U:                 No se puede procesar la operación
                            C->>U:                 💳 Entrega la tarjeta
                        end
                        end
                end
            end 
            rect rgb(230,230,255)

        critical                Confirmar con el servidor
        C->>S:                 Retirar importe solicitado
        S-->>C:                OK
        option                 No hay suficiente dinero en la cuenta
            S-->>C:            No hay suficiente dinero
            C-->>U:            No hay suficiente dinero
        option                Error del servidor
            rect rgb(255,230,230)
            S-->>C:            Error del servidor
            break                   Sistema no operativo
                C->>U:                 No se puede procesar la operación
                C->>U:                 💳 Entrega la tarjeta
            end
            end
        option              Timeout
            rect rgb(255,230,230)
            break                   Sistema no operativo
                C->>U:                 No se puede procesar la operación
                C->>U:                 💳 Entrega la tarjeta
            end
            end
        end
        end
        end
                    rect rgb(230,230,255)
        critical                Si no se ha conseguido una cantidad Correcta
            rect rgb(255,230,230)
                    break               
                        C-->>U:         💳 Entrega la tarjeta
                        C-->>U:         No se puede procesar la operación
                    end
                end
            end
            end

        C-->>U:                 💳 Entrega la tarjeta
        C-->>U:                 💰 Entrega el dinero
    end

```


# CRITICAL 

Hay tareas que pueden producir problemas potenciales, pero hasta que no intente hacer la tarea que puede producir el problema no se si el problema se va a a producir o no.

# ALT

HAY FLUJOS, que a priori me parecen problemas,
pero que no lo son realmente...


