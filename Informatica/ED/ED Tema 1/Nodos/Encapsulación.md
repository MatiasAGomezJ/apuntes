# Encapsulación
Permite a los objetos elegir qué información es publicada y qué información es escondida en el resto de los objetos. Por eso los objetos suelen presentar sus **métodos** como interfaces **públicas** y sus **atributos** como datos **privados o protegidas**, siendo **inaccesibles desde otros objetos**.

Las características que se pueden otorgar son:
- **Público**: **cualquier** clase puede acceder a cualquier atributo o método declarado como público y utilizarlo.
- **Protegido**: cualquier clase **heredada** puede acceder a cualquier atributo o método declarado como protegido a la clase madre y utilizarlo.
- **Privado**: **ninguna** clase puede acceder a un atributo o método declarado como privado y utilizarlo.

#ED 