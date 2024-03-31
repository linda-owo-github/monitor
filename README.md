# 自架設監控服務

## 背景與目的
![image](https://github.com/linda-owo-github/monitor/assets/66786888/f56cef1c-940f-47e8-84b7-49fa3a53d5b6)


  為了解決這個問題，我主動規劃並使用 Docker 架設了一套服務，包括 Traefik、cAdvisor、LibreNMS、Grafana、Prometheus、 Portainer、 Garylog，借助這些服務，我們可以即時監控網路設備的狀況，提前發現並解決潛在問題，有效地改善了系統的穩定性和可靠性，透過主動識別和解決潛在問題，降低了損失和系統異常

## 選擇服務

![image](https://github.com/linda-owo-github/monitor/assets/66786888/6e99db20-6f6d-4505-b3a4-95cace93f55b)


* Traefik：Traefik作為反向代理和負載均衡器，可以自動路由流量到正確的 Docker 容器，並根據需要動態調整負載
* Portainer：管理 Docker 容器、映像和容器網路的直觀界面，透過 Portainer，可以輕鬆地監視和操作容器
* LibreNMS：監控網路設備和服務器，提供關於系統狀態和性能
* Garylog：收集、分析和警報日誌數據，可以幫助監視應用程序和系統的運行狀態
* Prometheus： 收集時間序列數據
* Grafana： 則提供了靈活的圖表和面板，使您可以視覺化和分析監控數據
* cAdvisor：監控Docker容器的性能和資源使用情況


## 整合與效能評估
### 服務流程圖

以下是監控服務流程圖：

![Untitled diagram-2024-03-28-132704](https://github.com/linda-owo-github/monitor/assets/66786888/0723bd8a-6884-4e81-ba6c-8767f5d0beeb)



1. LibreNMS & Prometheus：LibreNMS 透過 Prometheus Exporter 將監控數據傳送到 Prometheus 中進行處理，同時使用 Pushgateway 進行監控數據的推送。 Alertmanager 負責處理和發送報警信息
2. Docker Container Monitoring：Docker Container 透過 cAdvisor 將數據傳送到 Prometheus 中進行監控和分析
3. Grafana & Traefik： ： Grafana 主要用於監控數據的可視化展示，而 Traefik 則用於服務的反向代理和路由
4. Portainer & Docker UI： Portainer 與 Docker 相連，主要用於容器的管理和操作

## 整合服務
![image](https://github.com/linda-owo-github/monitor/assets/66786888/c1ab3343-db67-4fe2-8251-f7e7ae59074f)

## 效能評估
![image](https://github.com/linda-owo-github/monitor/assets/66786888/acf0ef95-ef8f-46c9-9282-08318f4c24cd)



* Portainer 容器管理平台：  UI 介面，用於管理和操作 Docker 容器，提供了方便快捷的容器部署、監控和管理功能
* Grafana 圖表面板：主要使用於 Docker 容器和 LibreNMS 網絡監控所收集到的數據，透過 Grafana可以創建各種動態圖表和面板，以直觀方式呈現監控數據，快速了解系統狀態和性能
* Garylog 日誌監控和管理：追蹤系統活動、識別問題並進行故障排除
* LibreNMS 網絡監控： 即時檢測網絡故障和問題，並透過警報功能及時通知用戶，提高系統的可用性和可靠性

## 結論

![image](https://github.com/linda-owo-github/monitor/assets/66786888/b8db03e1-1e6d-4ab5-944d-61d49dd20e84)


* 監控系統的重要性：追蹤系統的狀態，識別並解決潛在問題，提高了系統可靠性和穩定性
* 性能優化：發現了性能方面的問題，這些問題導致系統效能不佳，可以透過監控和分析數據，能夠采取適當的措施來優化系統性能，提高系統的效率和性能
* 數據整合和視覺化：整合不同工具的數據並將其視覺化呈現，需要將來自不同來源的數據整合到單一平台中，並以清晰直觀的方式呈現，以便能夠輕松理解和分析數據
* 安全和隱私保護：在監控數據的收集、存儲和使用方面，需要確保符合相關的法規和標準，並采取必要的措施保護數據的安全性和隱私性










