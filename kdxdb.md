erDiagram
    DEPARTMENTS ||--|{ EMPLOYEE : department_id
    CLIENTS ||--o{ SYSTEMS : client_id
    EMPLOYEE ||--o{ SYSTEMS : system_director_id
    SYSTEMS ||--o{ DEVICES : system_id
    EMPLOYEE ||--o{ DEVICES : device_director_id
    DEVICES ||--o{ PROJECTS : device_id
    EMPLOYEE ||--o{ PROJECTS : project_director_id
    PROJECTS ||--o{ TASKS : project_id
    EMPLOYEE ||--o{ TASKS : task_director_id
    DEPARTMENTS ||--o{ TASK_TYPES : department_id
    TASK_TYPES ||--o{ TASKS : task_type_id
    TASKS ||--o{ REPORTS : task_id

    EMPLOYEE ||--o{ PROJECT_MANAGERS : employee_id
    PROJECT_MANAGERS }o--|| PROJECTS : project_id

    EMPLOYEE ||--o{ TASK_MANAGERS : employee_id
    TASK_MANAGERS }o--|| TASKS : task_id
    DEPARTMENTS ||--|| TASKS : department_id

    EMPLOYEE ||--o{ REPORT_VIEWERS : employee_id
    REPORT_VIEWERS }o--|| REPORTS : report_id
    EMPLOYEE ||--|{ REPORTS : employee_id
    EMPLOYEE ||--|{ REPORTS : checker_id

    DEPARTMENTS {
        INDEX id PK
        TEXT name "¼"
    }

    EMPLOYEE {
        INDEX id PK
        INDEX department_id FK "ID"
        TEXT name "]Æõ¼"
    }
    

    CLIENTS {
        INDEX id PK
        TEXT name "qæ¼"
    }

    SYSTEMS {
        INDEX id PK
        INDEX client_id FK "qæID"
        INDEX director_id FK "ÓCÒID"
        TEXT name "VXe¼Ì"
        TEXT model "^®"
        INT total_cnt "Ä°ÀÙ¶³ÝÀ"
        DATETIME created_at "ì¬ú"
        DATETIME updated_at "XVú"
    }

    DEVICES {
        INDEX id PK
        INDEX system_id FK "qæID"
        INDEX director_id FK "ÓCÒID"
        TEXT name "u¼Ì"
        TEXT model "^®"
        DATETIME created_at "ì¬ú"
        DATETIME updated_at "XVú"
    }

    PROJECTS{
        INDEX id PK
        INDEX device_id FK "uID"
        INDEX director_id FK "ÓCÒID"
        TEXT name "vWFNg¼Ì"
        ENUM type "íÊ(væ,VKó,ü¢ZP,sïZK)"
        ENUM status "óÔ(væ,is,®¹,êâ~)"
        DATETIME created_at "ì¬ú"
        DATETIME updated_at "XVú"
    }

    TASKS {
        INDEX id PK
        INDEX project_id FK "vWFNgID"
        INDEX director_id FK "ìÆÓCÒID"
        INDEX creater_id FK "ì¬ÒID"
        INDEX department_id FK "SID"
        INDEX type_id FK "íÊID"
        TEXT name "^XN¼Ì"
        ENUM status "óÔ(væ,is,®¹,êâ~)"
        DATETIME start_at "Jnú"
        DATETIME limit_at "úÀ"
        DATETIME end_at "®¹ú"
        DATETIME created_at "ì¬ú"
        DATETIME updated_at "XVú"
    }

    REPORTS {
        INDEX id PK
        INDEX task_id FK "ìÆID"
        INDEX creator_id FK "ñoÒID"
        INDEX checker_id FK "³FÒID"
        TEXT name "ñ¼"
        TEXT report_path "ñÛ¶æ"
        TEXT zip_path "Yt¿Û¶æ"
        DATETIME created_at "ì¬ú"
        DATETIME checked_at "³Fú"
        DATETIME updated_at "XVú"
    }

    PROJECT_MANAGERS {
        INDEX id PK
        INDEX project_id FK "ÄID"
        INDEX employee_id FK "SÒID"
    }

    TASK_MANAGERS {
        INDEX id PK
        INDEX task_id FK "ìÆID"
        INDEX employee_id FK "SÒID"
    }

    TASK_TYPES {
        INDEX id PK
        INDEX department_id FK "ID"
        TEXT name "ìÆ¼Ì"
    }

    REPORT_VIEWERS {
        INDEX id PK
        INDEX report_id FK "^XNID"
        INDEX employee_id FK "SÒID"
        DATETIME updated_at "XVú"
    }

    
