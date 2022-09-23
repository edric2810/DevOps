# Base helm chart

## Lời nói đầu

Tại sao lại có common helm chart ?
- Cấu trúc helm chart dựa theo cái chung của sự nhu cầu thường xuyên được khai báo trong helm chart.
- Để có thể dễ quản lý cấu trúc theo từng folder cần thiết để triển khai dịch vụ bằng helm chart.
- Dễ dàng tái sử dụng tính liên tục của helm chart.
- Dễ dàng bảo trì và tiếp tục phát triển services cho từng loại mọi trường.

Before you continue, ensure you meet the following requirements:

* You have installed the kubeneters (k8s) and helm chart on core linux.
* You have installed some plugins support for k8s
* You have knowlege basic about file yaml work then about helm chart.
* You have konwlege about bash script in linux.
* You have a basic understanding of graph theory.

## Lưu ý

- Không được custom source code của common helm chart.

## 1. Cách cài đặt helm chart on core linux:

Get file `get_helm.sh` để cài đặt helm chart:

```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
```

Cấp quyền cài đặt cho `file get_helm.sh`

```bash
chmod 700 get_helm.sh
```

Bắt đầu cài đặt helm chart. Lưu ý nhớ nằm đúng folder.
```bash
sudo bash ./get_helm.sh
```

- Sau khi nhập lệnh trên nếu có đòi mật khẩu hãy nhập mật khẩu của root password và trong quá trình cài nếu yêu cầu đồng ý thì chọn `yes`.
- Nếu có vấn đề về quá trình cài đặt vui lòng kiểm tra lại documents có đúng version hay không <a href="https://github.com/helm/charts">tại đây</a>

## 2. Cách sử dụng:

- Về base chart thì có 2 loại chart và được sử dụng theo tùy loại dự án được yêu cầu.



#### Do not do edit chart common.

``` Helm install [Name Service] helm/common -f helm/values/*.yaml -n [NAME SPACE]```

Don't forget apply configmap and secret

``` kubectl apply -f configs/*-config.yaml && kubectl apply -f secrets/secret*-secret.yaml -n [NAME SPACE]```
