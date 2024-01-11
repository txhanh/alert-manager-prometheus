Document for Alert Manager

Steps:
1. Create Telegram bot
    - Use @BotFather
    - /newbot
    - Get token from that bot
2. Add Telegram bot to the group
    - Get group ID
3. Config values file of helm-chart
    - Set: ruleNamespaceSelector: {}, this is default values, apply rules to all namespace (use prometheus-rule-selector.yaml)
    - Set: ruleSelector, value: dms4-alert-rules, kube-prometheus-stack (use prometheus-rule-selector.yaml)
    - Config alertmanager to send alert via telegram (use alertmanager-telegram-config.yaml)
4. Create a manifest file to define rules, then apply that file (use dms4-alert-rules.yaml)
    - This is YAML file with kind: PrometheusRule:
        + Kubernetes Nodes and Pods Rules:
            - Node CPU / RAM
            + Pod CPU / RAM
            + Node down
            + Kubernetes Node Memory Pressure
            + Kubernetes Node Disk Pressure
            + Kubernetes Pod Not Healthy
            + Kubernetes Pod Crash Looping
        + Kubernetes MariaDB rules:
            + Node down
            + Node restart
            + Too many connections
        + Kubernetest MongoDB rules:
            + Node down
            + Too many connections