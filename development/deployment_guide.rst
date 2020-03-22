Deployment Guide
=========================

Node Directory Structure
-------------------------

After a SEED node has been installed it will have the following directory
structure on the host system.

| /
|  ┣━ opt/
|  ┃    ┗━ seed/
|  ┃        ┣━ data/
|  ┃        ┃   ┣━ accounts/
|  ┃        ┃   ┣━ content/
|  ┃        ┃   ┣━ dynamic/
|  ┃        ┃   ┣━ logs/
|  ┃        ┃   ┣━ mom/
|  ┃        ┃   ┣━ static/
|  ┃        ┃   ┗━ telemetry/
|  ┃        ┣━ proxy/
|  ┃        ┃   ┣━ config/
|  ┃        ┃   ┃    ┗━ [F] version.conf
|  ┃        ┃   ┣━ services/
|  ┃        ┃   ┗━ [B] suisei.seed.proxy
|  ┃        ┣━ sc-<service name>/
|  ┃        ┃   ┣━ config/
|  ┃        ┃   ┃    ┗━ [F] version.conf
|  ┃        ┃   ┣━ services/
|  ┃        ┃   ┗━ [B] suisei.seed.services.<service name>
|  ┃        ┣━ supervisor/
|  ┃        ┃   ┣━ config/
|  ┃        ┃   ┃    ┗━ [F] version.conf
|  ┃        ┃   ┣━ services/
|  ┃        ┃   ┗━ [B] suisei.seed.supervisor
|  ┃        ┣━ updater/
|  ┃        ┃   ┣━ config/
|  ┃        ┃   ┃    ┗━ [F] version.conf
|  ┃        ┃   ┣━ services/
|  ┃        ┃   ┣━ updates/
|  ┃        ┃   ┗━ [B] suisei.seed.updater
|  ┃        ┗━ webui/
|  ┃            ┣━ config/
|  ┃            ┃    ┣━ [F] version.conf
|  ┃            ┃    ┗━ [F] webui.conf
|  ┃            ┣━ content/
|  ┃            ┃    ┣━ css/
|  ┃            ┃    ┣━ images/
|  ┃            ┃    ┣━ js/
|  ┃            ┃    ┗━ templates/
|  ┃            ┣━ services/
|  ┃            ┣━ templates/
|  ┃            ┣━ [B] suisei.seed.webui
|  ┃            ┣━ [F] webui.pem
|  ┃            ┗━ [F] webui_ca.pem
|  ┗━ var/
|       ┗━ logs/
|           ┗━ seed/
|               ┣━ proxy/
|               ┣━ sc-<service name>/
|               ┣━ supervisor/
|               ┣━ updater/
|               ┗━ webui/
