```mermaid
erDiagram
    MNP_Usuarios {
        string Id
        string Nombres
        string Apellidos
        string Usuario
        date FechaNacimiento
        string Telefono
        string Mail
        string Direccion
        bool IsDelete
        string Rol
        string ImagenPerfil
    }

    MNP_Comercios {
        string Id
        string IdZona
        string IdTipoComercio
        string Nombre
        string CIF
        string Telefono
        string Mail
        string Direccion
        string Geolocalizacion
        bool Participa
        bool IsDelete
        string Logo
    }

    MNP_Zonas {
        string Id
        string Nombre
        string Color
    }

    MNP_TiposComercio {
        string Id
        string Tipo
        string Icono
    }

    MNP_Visitas {
        string Id
        string IdUsuario
        string IdComercio
        date Fecha
    }

    MNP_Recompensas {
        string Id
        string IdUsuario
        string IdComercio
        string IdVisita
        string Concepto
        float Valor
        date Fecha
    }

    MNP_Temporadas {
        string Id
        date FechaInicio
        date FechaFin
        string Nombre
        string Descripcion
    }

    MNP_Participacion {
        string Id
        string IdUsuario
        string IdTemporada
        string IdComercio
        bool Participa
    }

    MNP_Usuarios ||--o{ MNP_Visitas : realiza
    MNP_Comercios ||--o{ MNP_Visitas : recibe

    MNP_Usuarios ||--o{ MNP_Recompensas : obtiene
    MNP_Comercios ||--o{ MNP_Recompensas : otorga
    MNP_Visitas ||--o{ MNP_Recompensas : genera

    MNP_Usuarios ||--o{ MNP_Participacion : participa
    MNP_Temporadas ||--o{ MNP_Participacion : pertenece
    MNP_Comercios ||--o{ MNP_Participacion : asociado

    MNP_Zonas ||--o{ MNP_Comercios : contiene
    MNP_TiposComercio ||--o{ MNP_Comercios : clasifica
