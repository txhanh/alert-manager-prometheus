Document for Alert Manager

Steps:
1. Create Telegram bot
    - Use @BotFather
    - /newbot
    - Get token from that bot
2. Add Telegram bot to the group
    - Get group ID
3. Config values file of helm-chart
    - Set: ruleNamespaceSelector: {} ==> this is default values, apply rules to all namespace
    - Set: ruleSelector, value: dms4-alert-rules, kube-prometheus-stack
    - Config alertmanager to send alert via telegram
4. Create a manifest file to define rules, then apply that file
    - This is YAML file with kind: PrometheusRule