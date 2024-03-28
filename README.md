# 自架設監控服務

## 背景與目的
  公司原有大量的網路管理設備，然而這些設備尚未進行整合管理，導致我們需要花費大量的時間和精力來分別監控每個服務的狀況，由於無法透過手機即時了解服務的運行狀態，許多問題往往只能在到達公司後才能發現，從而導致了數據損失和系統異常
  
  為了解決這個問題，我主動規劃並使用 Docker 架設了一套服務，包括 Traefik、cAdvisor、LibreNMS、Grafana、Prometheus、 Portainer、 Garylog，借助這些服務，我們可以即時監控網路設備的狀況，提前發現並解決潛在問題，有效地改善了系統的穩定性和可靠性，透過主動識別和解決潛在問題，降低了損失和系統異常

## 選擇服務
* Traefik：Traefik作為反向代理和負載均衡器，可以自動路由流量到正確的 Docker 容器，並根據需要動態調整負載
* Portainer：管理 Docker 容器、映像和容器網路的直觀界面，透過 Portainer，可以輕鬆地監視和操作容器
* LibreNMS：監控網路設備和服務器，提供關於系統狀態和性能
* Garylog：收集、分析和警報日誌數據，可以幫助您監視應用程序和系統的運行狀態，以及識別任何問題或異常
* Prometheus： 收集時間序列數據
* Grafana： 則提供了靈活的圖表和面板，使您可以視覺化和分析監控數據
* cAdvisor：監控Docker容器的性能和資源使用情況


## 整合與效能評估
### 服務流程圖

以下是監控服務流程圖：

![Untitled diagram-2024-03-28-132704](https://github.com/linda-owo-github/monitor/assets/66786888/7923608a-4b5d-422a-a012-b1f325786c02)

1. LibreNMS & Prometheus：LibreNMS 透過 Prometheus Exporter 將監控數據傳送到 Prometheus 中進行處理，同時使用 Pushgateway 進行監控數據的推送。 Alertmanager 負責處理和發送報警信息

2. Docker Container Monitoring：Docker Container 透過 cAdvisor 將數據傳送到 Prometheus 中進行監控和分析

3. Grafana & Traefik： ： Grafana 主要用於監控數據的可視化展示，而 Traefik 則用於服務的反向代理和路由

4. Portainer & Docker UI： Portainer 與 Docker 相連，主要用於容器的管理和操作

## 結論
* 監控系統的重要性：實時追蹤系統的狀態，及早識別並解決潛在問題，從而提高系統的可靠性和穩定性
* 性能優化：發現了一些性能方面的問題，導致系統效能不佳
* 數據整合和視覺化：整合不同工具的數據和視覺化呈現是一個挑戰，特別是在將監控數據集成到單一平台中
* 安全和隱私保護：確保監控數據的收集、存儲和使用符合相關法規和標準，並采取必要的措施保護數據的安全性和隱私性











