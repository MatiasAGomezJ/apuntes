Solución → Encriptar.
Dos posibilidades.
# FTPS
Extensión. Añade soporte para TLS (Transport layer security), capa por debajo que cifra.
Criptografía híbrida. También utiliza certificados X.509.
Usa los mismos comandos. Más fácil de implementar.
# SFTP
Secure File Transfer Protocol. Es una extensión de SSH para la transferencia de archivos.
Funciona sobre el canal de SSH.
Solo envía a través de un canal y solo en binario.
SFTP es más avanzado.

| 0                    | FTP     | FTPS        | SFTP                                   |
| -------------------- | ------- | ----------- | -------------------------------------- |
| Puerto               | 21      | 21          | 22                                     |
| Método encriptación  | No      | Certificado | Infraestructura de clave pública (PKI) |
| Método transferencia | Directa | Directa     | Túnel                                       |
