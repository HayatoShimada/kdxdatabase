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
        TEXT name "������"
    }

    EMPLOYEE {
        INDEX id PK
        INDEX department_id FK "����ID"
        TEXT name "�]�ƈ���"
    }
    

    CLIENTS {
        INDEX id PK
        TEXT name "�q�於"
    }

    SYSTEMS {
        INDEX id PK
        INDEX client_id FK "�q��ID"
        INDEX director_id FK "�ӔC��ID"
        TEXT name "�V�X�e������"
        TEXT model "�^��"
        INT total_cnt "İ�ٶ���"
        DATETIME created_at "�쐬��"
        DATETIME updated_at "�X�V��"
    }

    DEVICES {
        INDEX id PK
        INDEX system_id FK "�q��ID"
        INDEX director_id FK "�ӔC��ID"
        TEXT name "���u����"
        TEXT model "�^��"
        DATETIME created_at "�쐬��"
        DATETIME updated_at "�X�V��"
    }

    PROJECTS{
        INDEX id PK
        INDEX device_id FK "���uID"
        INDEX director_id FK "�ӔC��ID"
        TEXT name "�v���W�F�N�g����"
        ENUM type "���(�v��,�V�K��,����ZP,�s�ZK)"
        ENUM status "���(�v�撆,�i�s��,����,�ꎞ��~)"
        DATETIME created_at "�쐬��"
        DATETIME updated_at "�X�V��"
    }

    TASKS {
        INDEX id PK
        INDEX project_id FK "�v���W�F�N�gID"
        INDEX director_id FK "��ƐӔC��ID"
        INDEX creater_id FK "�쐬��ID"
        INDEX department_id FK "�S������ID"
        INDEX type_id FK "���ID"
        TEXT name "�^�X�N����"
        ENUM status "���(�v�撆,�i�s��,����,�ꎞ��~)"
        DATETIME start_at "�J�n��"
        DATETIME limit_at "����"
        DATETIME end_at "������"
        DATETIME created_at "�쐬��"
        DATETIME updated_at "�X�V��"
    }

    REPORTS {
        INDEX id PK
        INDEX task_id FK "���ID"
        INDEX creator_id FK "��o��ID"
        INDEX checker_id FK "���F��ID"
        TEXT name "�񍐏���"
        TEXT report_path "�񍐏��ۑ���"
        TEXT zip_path "�Y�t�����ۑ���"
        DATETIME created_at "�쐬��"
        DATETIME checked_at "���F��"
        DATETIME updated_at "�X�V��"
    }

    PROJECT_MANAGERS {
        INDEX id PK
        INDEX project_id FK "�Č�ID"
        INDEX employee_id FK "�S����ID"
    }

    TASK_MANAGERS {
        INDEX id PK
        INDEX task_id FK "���ID"
        INDEX employee_id FK "�S����ID"
    }

    TASK_TYPES {
        INDEX id PK
        INDEX department_id FK "����ID"
        TEXT name "��Ɩ���"
    }

    REPORT_VIEWERS {
        INDEX id PK
        INDEX report_id FK "�^�X�NID"
        INDEX employee_id FK "�S����ID"
        DATETIME updated_at "�X�V��"
    }

    
