# Mechalogix Web 製作
- https://www.mechalogix.com/

## Diary:
- 2024-03-01:First (init) -> Start Project
- 2024-03-04:

## Note:

### internationalization / translation
- https://www.youtube.com/watch?v=leyCGPGiy3E
- https://github.com/django/django/blob/main/django/conf/global_settings.py (doc)

1. Install gettext
    - http://ftp.gnome.org/pub/gnome/binaries/win32/dependencies/
    - https://mlocati.github.io/articles/gettext-iconv-windows.html

2. project/setting.py
    - from django.utils.translation import gettext_lazy as _
    - MIDDLEWARE = [
        ...
        'django.middleware.locale.LocaleMiddleware',
        ...
    ]
    - LANGUAGES = [
    ("en", _("English")),
    ("zh-hant", _("Traditional Chinese")),
    ]
    - LOCALE_PATHS = [
    os.path.join(BASE_DIR, 'locale'),
    ]

3. cmd:
    - django-admin makemessages -l en
    - django-admin makemessages -l zh_Hant
    - django-admin makemessages --all

4. Modify .po -> cmd:
    - django-admin compilemessages

#### rosetta
- pip install django-rosetta
1. settings.py
    - INSTALLED_APPS = [
        ...
        'rosetta',
    ]

2. project/urls
    - from django.conf.urls.i18n import i18n_patterns
    - path('rosetta/', include('rosetta.urls')),