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
        TEXT name "部署名"
    }

    EMPLOYEE {
        INDEX id PK
        INDEX department_id FK "部署ID"
        TEXT name "従業員名"
    }
    

    CLIENTS {
        INDEX id PK
        TEXT name "客先名"
    }

    SYSTEMS {
        INDEX id PK
        INDEX client_id FK "客先ID"
        INDEX director_id FK "責任者ID"
        TEXT name "システム名称"
        TEXT model "型式"
        INT total_cnt "ﾄｰﾀﾙｶｳﾝﾀ"
        DATETIME created_at "作成日"
        DATETIME updated_at "更新日"
    }

    DEVICES {
        INDEX id PK
        INDEX system_id FK "客先ID"
        INDEX director_id FK "責任者ID"
        TEXT name "装置名称"
        TEXT model "型式"
        DATETIME created_at "作成日"
        DATETIME updated_at "更新日"
    }

    PROJECTS{
        INDEX id PK
        INDEX device_id FK "装置ID"
        INDEX director_id FK "責任者ID"
        TEXT name "プロジェクト名称"
        ENUM type "種別(計画,新規受注,改造ZP,不具合ZK)"
        ENUM status "状態(計画中,進行中,完了,一時停止)"
        DATETIME created_at "作成日"
        DATETIME updated_at "更新日"
    }

    TASKS {
        INDEX id PK
        INDEX project_id FK "プロジェクトID"
        INDEX director_id FK "作業責任者ID"
        INDEX creater_id FK "作成者ID"
        INDEX department_id FK "担当部署ID"
        INDEX type_id FK "種別ID"
        TEXT name "タスク名称"
        ENUM status "状態(計画中,進行中,完了,一時停止)"
        DATETIME start_at "開始日"
        DATETIME limit_at "期限"
        DATETIME end_at "完了日"
        DATETIME created_at "作成日"
        DATETIME updated_at "更新日"
    }

    REPORTS {
        INDEX id PK
        INDEX task_id FK "作業ID"
        INDEX creator_id FK "提出者ID"
        INDEX checker_id FK "承認者ID"
        TEXT name "報告書名"
        TEXT report_path "報告書保存先"
        TEXT zip_path "添付資料保存先"
        DATETIME created_at "作成日"
        DATETIME checked_at "承認日"
        DATETIME updated_at "更新日"
    }

    PROJECT_MANAGERS {
        INDEX id PK
        INDEX project_id FK "案件ID"
        INDEX employee_id FK "担当者ID"
    }

    TASK_MANAGERS {
        INDEX id PK
        INDEX task_id FK "作業ID"
        INDEX employee_id FK "担当者ID"
    }

    TASK_TYPES {
        INDEX id PK
        INDEX department_id FK "部署ID"
        TEXT name "作業名称"
    }

    REPORT_VIEWERS {
        INDEX id PK
        INDEX report_id FK "タスクID"
        INDEX employee_id FK "担当者ID"
        DATETIME updated_at "更新日"
    }

    
