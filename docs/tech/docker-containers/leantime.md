---
title: Leantime
---

Leantime is a project management tool.

![Leantime screenshot](../images/leantime-1.png)

!!! info "Portainer"

    Leantime can't be started using a Portainer stack since it needs a .env file on startup.

## Resources

- [https://leantime.io](https://leantime.io)
- [https://docs.leantime.io/installation/docker](https://docs.leantime.io/installation/docker)

## Prerequisites

In the server root directory, create a folder called `leantime/`. `cd` into it and create the files `docker-compose.yml` and `.env`.

## Environment variables

The application requires some environment variables to be set when running the docker compose command. These variables are set in a .env file that must be created before hand. 

The sample file can be found on the Leantime Github page: [https://github.com/Leantime/docker-leantime/blob/master/sample.env](https://github.com/Leantime/docker-leantime/blob/master/sample.env).

??? note "Sample .env"

    ```php title=".env" linenums="1"
    # This is a sample configuration file with all possible configuration options.
    # If you don't want to maintain a file like this you can pass in all variables via Server Variables

    ## Minimum Configuration, these are required for installation

    LEAN_PORT = '8081'                                 # The port to expose and access Leantime
    LEAN_APP_URL = ''                                  # Base URL, needed for subfolder or proxy installs (including http:// or https://)
    LEAN_APP_DIR = ''                                  # Base of application without trailing slash (used for cookies), e.g, /leantime

    LEAN_DEBUG = 0                                     # Debug flag

    # Database - MySQL container
    MYSQL_ROOT_PASSWORD = 'changeme123'                # MySQL root password
    MYSQL_DATABASE = 'leantime'                        # Database name
    MYSQL_USER = 'lean'                                # Database username
    MYSQL_PASSWORD = 'changeme123'                     # Database password

    # Database - leantime container
    LEAN_DB_HOST = 'mysql_leantime'                    # Database host 
    LEAN_DB_USER = 'lean'                              # Database username (needs to be the same as MYSQL_USER)
    LEAN_DB_PASSWORD = 'changeme123'                   # Database password (needs to be the same as MYSQL_PASSWORD)
    LEAN_DB_DATABASE = 'leantime'                      # Database name (needs to be the same as MYSQL_DATABASE)
    LEAN_DB_PORT = '3306'                              # Database port


    ## Optional Configuration, you may omit these from your .env file

    ## Default Settings
    LEAN_SITENAME = 'Leantime'                         # Name of your site, can be changed later
    LEAN_LANGUAGE = 'en-US'                            # Default language
    LEAN_DEFAULT_TIMEZONE = 'America/Los_Angeles'      # Set default timezone
    LEAN_LOG_PATH = ''                                 # Default Log Path (including filename), if not set /logs/error.log will be used
    LEAN_DISABLE_LOGIN_FORM = false                    # If true then don't show the login form (useful only if additional auth method[s] are available)

    ## Session Management
    LEAN_SESSION_PASSWORD = '3evBlq9zdUEuzKvVJHWWx3QzsQhturBApxwcws2m'  # Salting sessions, replace with a strong password
    LEAN_SESSION_EXPIRATION = 28800                    # How many seconds after inactivity should we logout?  28800seconds = 8hours
    LEAN_SESSION_SECURE = false                        # Cookies only served via https

    ## Look & Feel, these settings are available in the UI and can be overwritten there.
    LEAN_LOGO_PATH = '/dist/images/logo.svg'           # Default logo path, can be changed later
    LEAN_PRINT_LOGO_URL = '/dist/images/logo.png'      # Default logo URL use for printing (must be jpg or png format)
    LEAN_DEFAULT_THEME = 'default'                     # Default theme
    LEAN_PRIMARY_COLOR = '#006d9f'                     # Primary Theme color
    LEAN_SECONDARY_COLOR =' #00a886'                   # Secondary Theme Color


    ## Fileuploads

    # Local File Uploads
    LEAN_USER_FILE_PATH = 'userfiles/'                 # Local relative path to store uploaded files (if not using S3)
    LEAN_DB_BACKUP_PATH = 'backupdb/'                  # Local relative path to store backup files, need permission to write

    # S3 File Uploads
    LEAN_USE_S3 = false                                # Set to true if you want to use S3 instead of local files
    LEAN_S3_KEY = ''                                   # S3 Key
    LEAN_S3_SECRET = ''                                # S3 Secret
    LEAN_S3_BUCKET = ''                                # Your S3 bucket
    LEAN_S3_USE_PATH_STYLE_ENDPOINT = false            # Sets the endpoint style: false => https://[bucket].[endpoint] ; true => https://[endpoint]/[bucket]
    LEAN_S3_REGION = ''                                # S3 region
    LEAN_S3_FOLDER_NAME = ''                           # Foldername within S3 (can be empty)
    LEAN_S3_END_POINT = null                           # S3 EndPoint S3 Compatible (https://sfo2.digitaloceanspaces.com)

    ## Email
    LEAN_EMAIL_RETURN = ''                             # Return email address, needs to be valid email address format
    LEAN_EMAIL_USE_SMTP = false                        # Use SMTP? If set to false, the default php mail() function will be used
    LEAN_EMAIL_SMTP_HOSTS = ''                         # SMTP host
    LEAN_EMAIL_SMTP_AUTH = true                        # SMTP authentication required
    LEAN_EMAIL_SMTP_USERNAME = ''                      # SMTP username
    LEAN_EMAIL_SMTP_PASSWORD = ''                      # SMTP password
    LEAN_EMAIL_SMTP_AUTO_TLS = true                    # SMTP Enable TLS encryption automatically if a server supports it
    LEAN_EMAIL_SMTP_SECURE = ''                        # SMTP Security protocol (usually one of: TLS, SSL, STARTTLS)
    LEAN_EMAIL_SMTP_SSLNOVERIFY = false                # SMTP Allow insecure SSL: Don't verify certificate, accept self-signed, etc.
    LEAN_EMAIL_SMTP_PORT = ''                          # Port (usually one of 25, 465, 587, 2526)

    ## LDAP
    LEAN_LDAP_USE_LDAP = false                         # Set to true if you want to use LDAP
    LEAN_LDAP_LDAP_DOMAIN = ''                         # Domain name after username@ so users can login without domain definition
    LEAN_LDAP_LDAP_TYPE = 'OL'                         # Select the correct directory type. Currently Supported: OL - OpenLdap, AD - Active Directory
    LEAN_LDAP_HOST = ''                                # FQDN
    LEAN_LDAP_PORT = 389                               # Default Port
    LEAN_LDAP_URI = ''                                 # LDAP URI as alternative to hostname and port. Uses ldap://hostname:port
    LEAN_LDAP_DN = ''                                  # Location of users, example: CN=users,DC=example,DC=com
                                                      # Leantime->Ldap attribute mapping
    LEAN_LDAP_KEYS="{
            \"username\":\"uid\",
            \"groups\":\"memberOf\",
            \"email\":\"mail\",
            \"firstname\":\"displayname\",
            \"lastname\":\"\",
            \"phone\":\"telephoneNumber\",
            \"jobTitle\":\"title\"
            \"jobLevel\":\"level\"
            \"department\":\"department\"

    }"

    # For AD use these default attributes
    # LEAN_LDAP_KEYS="{
    #        \"username\":\"cn\",
    #        \"groups\":\"memberOf\",
    #        \"email\":\"mail\",
    #        \"firstname\":\"givenName\",
    #        \"lastname\":\"sn\",
    #        \"phone\":\"telephoneNumber\",
    #        \"jobTitle\":\"title\"
    #        \"jobLevel\":\"level\"
    #        \"department\":\"department\"
    #      }"

    LEAN_LDAP_DEFAULT_ROLE_KEY = 20;                   # Default Leantime Role on creation. (set to editor)

    # Default role assignments upon first login.
    # optional - Can be updated later in user settings for each user
    LEAN_LDAP_GROUP_ASSIGNMENT="{
                  \"5\": {
                    \"ltRole\":\"readonly\",
                    \"ldapRole\":\"readonly\"
                  },
                  \"10\": {
                    \"ltRole\":\"commenter\",
                      \"ldapRole\":\"commenter\"
                  },
                  \"20\": {
                    \"ltRole\":\"editor\",
                      \"ldapRole\":\"editor\"
                  },
                  \"30\": {
                    \"ltRole\":\"manager\",
                      \"ldapRole\":\"manager\"
                  },
                  \"40\": {
                    \"ltRole\":\"admin\",
                      \"ldapRole\":\"administrators\"
                  },
                  \"50\": {
                    \"ltRole\":\"owner\",
                    \"ldapRole\":\"administrators\"
                  }
    }"

    ## OpenID Connect
    # required
    LEAN_OIDC_ENABLE = false
    LEAN_OIDC_CLIENT_ID =
    LEAN_OIDC_CLIENT_SECRET =

    # required - the URL for your provider (examples down below)
    #LEAN_OIDC_PROVIDER_URL =

    #Create User if it doesn't exist in Leantime db, otherwise fail login
    LEAN_OIDC_CREATE_USER = false

    # Default role for users created via OIDC (20 is editor)
    LEAN_OIDC_DEFAULT_ROLE = 20

    # optional - these will be read from the well-known configuration if possible
    #LEAN_OIDC_AUTH_URL_OVERRIDE =
    #LEAN_OIDC_TOKEN_URL_OVERRIDE =
    #LEAN_OIDC_JWKS_URL_OVERRIDE =
    #LEAN_OIDC_USERINFO_URL_OVERRIDE =

    # optional - override the public key for RSA validation
    #LEAN_OIDC_CERTIFICATE_STRING =
    #LEAN_OIDC_CERTIFICATE_FILE =

    # optional - override the requested scopes
    #LEAN_OIDC_SCOPES =

    # optional - override the keys used for these fields
    #LEAN_OIDC_FIELD_EMAIL =
    #LEAN_OIDC_FIELD_FIRSTNAME =
    #LEAN_OIDC_FIELD_LASTNAME =
    #LEAN_OIDC_FIELD_PHONE =
    #LEAN_OIDC_FIELD_JOBTITLE =
    #LEAN_OIDC_FIELD_JOBLEVEL=
    #LEAN_OIDC_FIELD_DEPARTMENT =

    ## OpenID Connect setting for GitHub
    #LEAN_OIDC_PROVIDER_URL = https://token.actions.githubusercontent.com/
    #LEAN_OIDC_AUTH_URL_OVERRIDE = https://github.com/login/oauth/authorize
    #LEAN_OIDC_TOKEN_URL_OVERRIDE = https://github.com/login/oauth/access_token
    #LEAN_OIDC_USERINFO_URL_OVERRIDE = https://api.github.com/user,https://api.github.com/user/emails
    #LEAN_OIDC_SCOPES = user:email,read:user
    #LEAN_OIDC_FIELD_EMAIL = 0.email
    #LEAN_OIDC_FIELD_FIRSTNAME = name


    ## Redis (for session storage and cache)
    LEAN_USE_REDIS = false                             # Set to true to use redis as session cache
    LEAN_REDIS_URL = ''                                # Add URL path such as tcp://1.2.3.4:6379. If you are using a password, add ?auth=yourverycomplexpasswordhere to your URL
    LEAN_REDIS_HOST = ''
    LEAN_REDIS_PORT = 6379
    LEAN_REDIS_PASSWORD = ''
    LEAN_REDIS_SCHEME = ''

    ## Rate limiting
    LEAN_RATELIMIT_GENERAL = 1000
    LEAN_RATELIMIT_API = 10
    LEAN_RATELIMIT_AUTH = 20
    ```

## Docker Compose

```yaml title="docker-compose.yml" linenums="1"
---
services:
  leantime_db:
    image: mysql:8.4
    container_name: mysql_leantime
    volumes:
      - db_data:/var/lib/mysql
    restart: unless-stopped
    env_file: ./.env
    networks:
      - leantime-net
    command: --character-set-server=UTF8MB4 --collation-server=UTF8MB4_unicode_ci

  leantime:
    image: leantime/leantime:latest
    container_name: leantime
    restart: unless-stopped
    env_file: ./.env
    networks:
      - leantime-net
    volumes:
      - public_userfiles:/var/www/html/public/userfiles
      - userfiles:/var/www/html/userfiles
      - plugins:/var/www/html/app/Plugins
    ports:
      - "${LEAN_PORT}:80"
    depends_on:
      - leantime_db

volumes:
  db_data:
  userfiles:
  public_userfiles:
  plugins:

networks:
  leantime-net:
```

### Configuration

- **env_file** - Path to the .env file.
- **Ports** - Default port for the UI is `8081`.

## Deploy the container

Since Leantime requires the .env file to exist before running Docker Compose, it can't be started using a Portainer stack.

Run the Docker Compose file in the terminal:

```bash
docker compose up -d
```

## Setup

Start the application setup by going to the URL:

**Setup:** http://server-ip:8081/install

## Login

**UI:** http://server-ip:8081