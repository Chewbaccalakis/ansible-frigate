# Ansible-frigate-role

Ansible Role to deploy frigate w/ caddy and oauth2-proxy

### Variables
#### Docker Compose Vars
##### Caddy Configuration
caddy_http_port: "80"
caddy_https_port: "443"
public_url: "frigate.example.com"

##### OAuth2 Proxy Configuration
oauth2_proxy_image: "quay.io/oauth2-proxy/oauth2-proxy:v7.8.1"

##### Frigate Configuration
frigate_image: "ghcr.io/blakeblackshear/frigate:stable"
frigate_plus: false
frigate_plus_api_key: ""
tpu_enabled: false
tpu_device: "/dev/apex_0:/dev/apex_0"
frigate_config_dir: "/frigate"
frigate_storage_dir: "/frigate/storage"
frigate_tmpfs_size: 1000000000
frigate_webrtc_port: "8555"
frigate_rtsp_port: "8554"
expose_api: false # DO NOT ENABLE if unsure, exposes unauthenticated access on api port
frigate_api_port: "5000"

##### Frigate Notify Configuration
frigate_notify_enabled: false
frigate_notify_image: "ghcr.io/0x2142/frigate-notify:latest"
frigate_notify_port: "8000"
frigate_notify_timezone: "America/Los_Angeles"

##### Neolink Configuration
neolink_enabled: false
neolink_image: "quantumentangledandy/neolink:latest"

#### Frigate Vars
coral_type: "edgetpu"
coral_device: "pci"

#### Oauth2 proxy vars
oauth2_proxy_http_address: "0.0.0.0:4180"
oauth2_proxy_cookie_secret: "your-secret"
oauth2_proxy_email_domains: "trochalakis.com"
oauth2_proxy_cookie_secure: "false"
oauth2_proxy_upstreams: "https://frigate.example.com"
oauth2_proxy_cookie_domains: [".example.com"]
oauth2_proxy_whitelist_domains: [".example.com"]
oauth2_proxy_scope: "openid email profile"
oauth2_proxy_client_secret: "your-client-secret"
oauth2_proxy_client_id: "your-client-id"
oauth2_proxy_redirect_url: "https://frigate.example.com/oauth2/callback"
oauth2_proxy_oidc_issuer_url: "https://auth.example.com"
oauth2_proxy_provider: "oidc"
oauth2_proxy_provider_display_name: "OIDC"

#### Frigate Notify Vars
app_mode: "events"
app_api_enabled: true
app_api_port: 8000

frigate_server: "http://frigate:5000"
frigate_ignoressl: true
frigate_public_url: ""
frigate_headers: {}
frigate_startup_check_attempts: 5
frigate_startup_check_interval: 30
frigate_webapi_enabled: true
frigate_webapi_interval: 30

alerts_general_title: "Frigate Alert"
alerts_general_nosnap: "allow"
alerts_general_snap_bbox: false
alerts_general_snap_timestamp: false
alerts_general_snap_crop: false
alerts_general_max_snap_retry: 10
alerts_general_notify_once: false
alerts_general_notify_detections: false
alerts_general_recheck_delay: 0
alerts_general_audio_only: "allow"

alerts_zones_unzoned: "allow"

##### MQTT
frigate_mqtt_enabled: false
frigate_mqtt_server: ""
frigate_mqtt_port: ""
frigate_mqtt_clientid: ""
frigate_mqtt_username: ""
frigate_mqtt_password: ""
frigate_mqtt_topic_prefix: ""

##### Discord
alerts_discord_enabled: false
alerts_discord_webhook: ""
alerts_discord_template: ""

##### Gotify
alerts_gotify_enabled: false
alerts_gotify_server: ""
alerts_gotify_token: ""
alerts_gotify_ignoressl: ""
alerts_gotify_template: ""

##### Mattermost
alerts_mattermost_enabled: false
alerts_mattermost_webhook: ""
alerts_mattermost_channel: ""
alerts_mattermost_username: ""
alerts_mattermost_priority: ""
alerts_mattermost_ignoressl: ""
alerts_mattermost_headers: {}
alerts_mattermost_template: ""

##### ntfy
alerts_ntfy_enabled: false
alerts_ntfy_server: ""
alerts_ntfy_topic: ""
alerts_ntfy_ignoressl: ""
alerts_ntfy_headers: {}
alerts_ntfy_template: ""

##### Pushover
alerts_pushover_enabled: false
alerts_pushover_token: ""
alerts_pushover_userkey: ""
alerts_pushover_devices: ""
alerts_pushover_sound: ""
alerts_pushover_priority: ""
alerts_pushover_retry: ""
alerts_pushover_expire: ""
alerts_pushover_ttl: ""
alerts_pushover_template: ""

#### Signal
alerts_signal_enabled: false
alerts_signal_server: ""
alerts_signal_account: ""
alerts_signal_recipients: ""
alerts_signal_ignoressl: ""
alerts_signal_template: ""

#### SMTP
alerts_smtp_enabled: false
alerts_smtp_server: ""
alerts_smtp_port: ""
alerts_smtp_tls: ""
alerts_smtp_user: ""
alerts_smtp_password: ""
alerts_smtp_recipient: ""
alerts_smtp_template: ""

##### Telegram
alerts_telegram_enabled: false
alerts_telegram_chatid: ""
alerts_telegram_token: ""
alerts_telegram_template: ""

##### Webhook
alerts_webhook_enabled: false
alerts_webhook_server: ""
alerts_webhook_ignoressl: ""
alerts_webhook_method: ""
alerts_webhook_params: {}
alerts_webhook_headers: {}
alerts_webhook_template: ""

##### Monitor
monitor_enabled: false
monitor_url: ""
monitor_interval: ""
monitor_ignoressl: ""

### Notes
    - Built to be behind another reverse proxy. Built in caddy instance does not handle tls
