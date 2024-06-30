

특정 ip 대역대 감시
watch 'ipvsadm -Ln | grep -A 2 "UDP  10.96.0.10:53"'
watch -d -n 0.1 'ipvsadm -Ln | grep -A 2 "UDP  10.96.0.10:53"'

kubectl -n kube-system rollout restart daemonset kube-proxy


sudo ipvsadm --clear

sudo modprobe ip_vs
sudo modprobe ip_vs_rr
sudo modprobe ip_vs_wrr
sudo modprobe ip_vs_sh
sudo modprobe nf_conntrack_ipv4

모듈 자동 로드
echo -e "ip_vs\nip_vs_rr\nip_vs_wrr\nip_vs_sh\nnf_conntrack_ipv4" | sudo tee /etc/modules-load.d/ipvs.conf


sudo iptables --policy INPUT   ACCEPT
sudo iptables --policy OUTPUT  ACCEPT
sudo iptables --policy FORWARD ACCEPT
 
sudo iptables -Z # zero counters
sudo iptables -F # flush (delete) rules
sudo iptables -X # delete all extra chains
 
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
sudo iptables -t raw -F
sudo iptables -t raw -X

kubectl delete pod ghost-deployment-5cfb4f646-bc7bd --force --grace-period=0 -n default
kubectl delete pod ghost-deployment-5cfb4f646-pknpm --force --grace-period=0 -n default


kubectl get cm -n kube-system
k edit cm kube-proxy -n kube-system
mode 수정
kubectl -n kube-system rollout restart daemonset kube-proxy


https://github.com/kubernetes/kubernetes/issues/115526
https://www.slideshare.net/slideshow/233-large-containerclusternetworkloadbalancing/119166390#34