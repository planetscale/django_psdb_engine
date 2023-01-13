# PlanetScale support for Django

Because Django's default migrations use foreign key constraints, and [PlanetScale doesn't support foreign key constraints](https://planetscale.com/docs/learn/operating-without-foreign-key-constraints), you need to disable them globally in Django.

This package subclasses the existing `django.db.backends.mysql` database engine to change the `supports_foreign_keys` value to `False`. This allows you to run Django migrations without issue.

## Add it to your project

1. In the root of your project:

```bash
git clone https://github.com/planetscale/django_psdb_engine.git
```

2. In your `settings.py` file, find the `DATABASES` object and modify the `ENGINE` field as follows:

```py
DATABASES = {
    'default': {
        'ENGINE': 'django_psdb_engine',
    }
}
```

3. Run migrations with:

```bash
python manage.py migrate
```

**Note**: The `doc` and `.github/workflows` folders are for our licensing and not required to turn off foreign key constraints.
