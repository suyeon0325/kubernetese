# kubernetese-etcd
쿠버네티스 etcd 학습자료를 정리했습니다. 

--

## etcd
ETCD는 간단, 안전, 빠른 신뢰할 수 있는 분산형 키-값 저장소

## etcdctl이 etcd API 서버에 인증할 수 있도록, 인증서 파일의 경로를 지정해야 함.
## 인증서 파일은 다음 경로의 etcd-master에서 사용할 수 있음
--cacert /etc/kubernetes/pki/etcd/ca.crt
--cert /etc/kubernetes/pki/etcd/server.crt
--key /etc/kubernetes/pki/etcd/server.key

## 명령어가 작동하려면, etcdctl API버전과 인증서 파일 경로를 지정해야 함 (아래 최종양식)
kubectl exec etcd-master -n kube-system -- sh -c "ETCDCTL_API=3 etcdctl get / --prefix --keys-only --limit=10 --cacert /etc/kubernetes/pki/etcd/ca.crt --cert /etc/kubernetes/pki/etcd/server.crt --key /etc/kubernetes/pki/etcd/server.key"