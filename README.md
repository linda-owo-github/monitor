# monitor
公司原有大量的網路管理設備，然而這些設備尚未進行整合管理，導致我們需要花費大量的時間和精力來分別監控每個服務的狀況，由於無法透過手機即時了解服務的運行狀態，許多問題往往只能在到達公司後才能發現，從而導致了數據損失和系統異常。

為了解決這個問題，我主動規劃並使用 Docker 架設了一套服務，包括 Traefik、cAdvisor、LibreNMS、Grafana、Prometheus 和 Garylog，借助這些服務，我們可以即時監控網路設備的狀況，提前發現並解決潛在問題，有效地改善了系統的穩定性和可靠性，透過主動識別和解決潛在問題，降低了損失和系統異常






以下是使用 LibreNMS、Prometheus、Pushgateway 和 Grafana 的流程图：



![Untitled diagram-2024-03-28-132704](https://github.com/linda-owo-github/monitor/assets/66786888/7923608a-4b5d-422a-a012-b1f325786c02)



1. LibreNMS 使用 SNMP 監控網路設備，並將收集到的指標推送到 Prometheus。
2. Prometheus 接收到指標後存儲並進行相應的指標分析。
3. Pushgateway 接收到 Prometheus 收集的指標，然後將其推送給 Grafana。
4. Grafana 通過網頁瀏覽器查詢 Prometheus 存儲的指標，並將其可視化展示在儀表板上，用戶可以通過 Grafana 查看和分析指標數據。
