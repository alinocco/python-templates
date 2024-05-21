# SQLAlchemy

1. Скачать SQLAlchemy и Alembic:
```
poetry add sqlalchemy alembic
```

2. Инициализировать Alembic:
```
alembic init migrations
```

3. Установить в alembic.ini ссылку на БД:
```
sqlalchemy.url = postgresql+asyncpg://asyncshop:asyncshop@localhost/asyncshop
```

4. Установить в migrations/env.py:
```
# add your model's MetaData object here
# for 'autogenerate' support
from models import Base
target_metadata = Base.metadata
# target_metadata = None
```

5. Создать базовую модель в models.py и наследовать от неё все модели:
```
from sqlalchemy.orm import declarative_base

Base = declarative_base()

class UserModel(Base):
...
```

6. Создать миграцию:
```
alembic revision --autogenerate -m "migration name"
```

7. Применить миграцию:
```
alembic upgrade heads
```
