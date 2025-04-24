```mermaid
erDiagram
    FUNKOS ||--|| CATEGORIAS : pertenece
    FUNKOS ||--|| MARCAS : es_de
    USUARIOS ||--o{ COLECCIONES : tiene
    FUNKOS ||--o{ COLECCIONES : pertenece_a

    FUNKOS {
        int id
        string nombre
        int categoria_id
        int marca_id
        float precio
    }

    CATEGORIAS {
        int id
        string nombre
    }

    MARCAS {
        int id
        string nombre
    }

    USUARIOS {
        int id
        string nombre
        string email
    }

    COLECCIONES {
        int id
        int usuario_id
        int funko_id
        date fecha_adquisicion
    }
