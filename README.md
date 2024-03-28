# 自架設監控服務

  公司原有大量的網路管理設備，然而這些設備尚未進行整合管理，導致我們需要花費大量的時間和精力來分別監控每個服務的狀況，由於無法透過手機即時了解服務的運行狀態，許多問題往往只能在到達公司後才能發現，從而導致了數據損失和系統異常
  為了解決這個問題，我主動規劃並使用 Docker 架設了一套服務，包括 Traefik、cAdvisor、LibreNMS、Grafana、Prometheus、 Portainer、 Garylog，借助這些服務，我們可以即時監控網路設備的狀況，提前發現並解決潛在問題，有效地改善了系統的穩定性和可靠性，透過主動識別和解決潛在問題，降低了損失和系統異常

以下是監控服務流程圖：

![Untitled diagram-2024-03-28-132704](https://github.com/linda-owo-github/monitor/assets/66786888/7923608a-4b5d-422a-a012-b1f325786c02)

1. LibreNMS & Prometheus：LibreNMS 透過 Prometheus Exporter 將監控數據傳送到 Prometheus 中進行處理，同時使用 Pushgateway 進行監控數據的推送。 Alertmanager 負責處理和發送報警信息

2. Docker Container Monitoring：Docker Container 透過 cAdvisor 將數據傳送到 Prometheus 中進行監控和分析

3. Grafana & Traefik： ： Grafana 主要用於監控數據的可視化展示，而 Traefik 則用於服務的反向代理和路由

4. Portainer & Docker UI： Portainer 與 Docker 相連，主要用於容器的管理和操作
