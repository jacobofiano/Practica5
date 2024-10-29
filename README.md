# Practica5
#### Servizos

#### bind9

- **image**: `internetsystemsconsortium/bind9:9.18`  
  Especifica a imaxe de Docker que se usará para o servizo. Neste caso, está utilizando a imaxe oficial de Bind9 mantida polo Internet Systems Consortium (ISC), na versión `9.18`.

- **container_name**: `bind9`  
  Define o nome do contedor para facilitar a súa identificación. Aquí, o contedor chamarase `bind9`.

- **ports**:
  
  - `54:53/tcp`  
    Mapea o porto `53` TCP do contedor ao porto `54` TCP no host. O porto `53` é o porto estándar para consultas DNS. Cambiouse ao porto `54` no host, polo que as consultas DNS deberán enviarse a este porto en vez do porto estándar.
  
  - `54:53/udp`  
    Similar ao anterior, este mapeo configura o porto `53` UDP do contedor (necesario para consultas DNS) ao porto `54` UDP no host.

  - `127.0.0.1:953:953/tcp`  
    Expón o porto `953` TCP do contedor ao porto `953` TCP na interface `localhost` do host (127.0.0.1). Este porto é utilizado por defecto por Bind9 para administración a través de `RNDC` (Remote Name Daemon Control), permitíndolle a Bind9 aceptar comandos de control. Ao configurar este porto para escoitar soamente en `localhost`, restrínxeo ao acceso local, aumentando a seguridade.

### Executar o Contedor

Para iniciar o contedor, executa o seguinte comando:
docker-compose up -d