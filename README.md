# -Kubernetes
1. 
* Kubernetes là mốt công cụ hay phần mềm đươc sử dụng để quản lý docker containers trong môi trường cụm (cluseter). Nó được biết như là k8s được Google phát triển. 

* Trong Kubernetes có một node master và nhiều node khác. Những node cluster như là worker node hoặc Minion. Từ node master chúng ta sẽ quản lý cụm và những node của nó sử dụng lệnh kubeadm và kubectl.

* Có 3 cách để cài đặt Kubernetes.

  + Minikube (một cluster node đơn)
  
  + Kops (nhiều node kubernetes được tổ chức trong AWS ) 
 
  + Kubeadm ?
  
* Mô hình bài lap: Cài đặt trên 4 server Centos 7 Core và trong đó có một server mà node master và 3 con còn lại sẽ là các worker node hoặc minion

* Trên Master node có các thành phần sau cần được cài đặt.

  - API Server: Nó cung cấp API kubernetes sử dụng Jason/Yaml trên http, các trạng thái của API được lưu trữ tại etcd
  - Scheduler: là chương trình trên master node thực hiện các scheduling tasks như chạy các containers trong các worker node dựa trên tài nguyên có sẵn
  - Controller Manager: Nó sẽ giám sát các controllers replication và tạo các pod để duy trì các trạng thái mong muốn
  - etcd: là cơ sở dữ liệu cặp giá trị khóa (Key-Value). Nó lưu trữ các dữ liệu cấu hình của cluster và các trạng thái của cluster.
  - Kubectl utility: là tiện ích lệnh nó kết nối để API Server trên port 6443. Nó được sử dụng bởi người quản trị để tại pods, service, ...
  
  * Trên các Worker Nodes gồm các thành phần được cài đặt. 
  
   - Kubelet: là một agent chạy trên mọi worker node. Nó kết nối đến docker và nó thực hiện việc tạo, khởi động, xóa các container.
   - Kube-proxy: Nó định tuyến lưu lượng tới các containers thích hợp dựa trên địa chỉ IP và Port của các request đến.
   - Pod: nó như là các container đa tầng hay group các containers (container được triển khai trên worker node đơn hoặc docker host). 
   
   ## 2.  Install: 
