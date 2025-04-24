```mermaid
erDiagram
    %% Tablas principales
    Tipo_Comercio {
        int Id PK
        nvarchar Tipo
    }
    Tabla_Zonas {
        int Id PK
        nvarchar Nombre
    }
    Tabla_Comercios {
        int Id PK
        int IdZona FK
        int IdTipoComercio FK
        nvarchar Nombre
        nvarchar Direccion
        nvarchar Mail
        nvarchar Telefono
    }
    Tabla_Usuarios {
        int Id PK
        nvarchar Nombre
        nvarchar Apellidos
        date FechaNacimiento
        nvarchar Telefono
        nvarchar Email
        nvarchar Rol
        nvarchar Direccion
        bit IsDelete
    }
    Tabla_Visitas {
        int Id PK
        int Id_usuario FK
        int Id_comercio FK
        datetime Fecha
    }
    Tabla_Recompensas {
        int Id PK
        int Id_usuario FK
        int Id_comercio FK
        int Id_visita FK
        nvarchar Concepto
        decimal Valor
        datetime Fecha
    }
    Temporadas {
        int Id PK
        date FechaInicio
        date FechaFin
        bit IsActiva
    }
    Tabla_Participacion {
        int Id PK
        int Id_usuario FK
        int Id_temporada FK
        bit Participa
    }

    %% Relaciones
    Tipo_Comercio ||--o{ Tabla_Comercios       : define
    Tabla_Zonas    ||--o{ Tabla_Comercios       : contiene
    Tabla_Usuarios ||--o{ Tabla_Visitas         : hace
    Tabla_Comercios||--o{ Tabla_Visitas         : recibe
    Tabla_Usuarios ||--o{ Tabla_Recompensas     : recibe
    Tabla_Comercios||--o{ Tabla_Recompensas     : otorga
    Tabla_Visitas  ||--o{ Tabla_Recompensas     : genera
    Temporadas     ||--o{ Tabla_Participacion   : organiza
    Tabla_Usuarios ||--o{ Tabla_Participacion   : participa
