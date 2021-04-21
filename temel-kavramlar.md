## Kubernetes (k8s) Nedir?

Kubernetes (**k8s**) açık kaynak olarak geliştirlen bir container orkestrasyon platformudur. Başlıca özelliklerinin arasında uygulamaların dağıtımı, ölçeklenmesi ve yönetilmesi bulunmaktadır. 

Kubernetes üzerinde obje oluşturmak, düzenlemek veya silmek için **kubectl** komut arayüzü kullanılabilir. Kubectl üzerinde gireceğiniz komutlar arka tarafta Kubernetes API 'lerine iletilerek işlemler gerçekleştirilir.

**Kubernetesi API** 'lerini kendi uygulamalarınız üzerinde de doğrudan kullanabilirsiniz.

## Pods
Kubernetes üzerinde çalışan her bir prosesi temsil etmektedir. Genel kabul görmüş kullanım şekli her bir pod üzerinde bir container çalıştırılmasıdır. Tabiki bunun istisna olduğu durumlar da mevcuttur.

Podları listele:
```
kubectl get pods
```
Podları ayrıntılı bilgiler içerecek şekilde listele:
```
kubectl get pods -o wide
```
Belli bir node üzerinde çalışan tüm pods listesi:

```
kubectl get pods --field-selector=spec.nodeName=[server-name]
```
## Replica Set
Kubernetes üzerinde tanımlanan bir yaml file ile belirtilen sayı kadar pod kopyası ayağa kaldırdır. Ölen podların yerine yenisini koyar. 

Replica Set'leri listeleme:

```shell
kubectl get rs
```
Replica set 'in ayrıntılı bir şekilde durumunu kontrol etmek:

```shell
kubectl describe rs/frontend
```

İlgili yaml Replica Seti k8s üzerinde uygulamak için.

```shell
kubectl apply -f https://kubernetes.io/examples/pods/pod-rs.yaml
```

Örnek bir replica set yaml:

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: frontend
  labels:
    app: guestbook
    tier: frontend
spec:
  replicas: 3
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      labels:
        tier: frontend
    spec:
      containers:
      - name: php-redis
        image: gcr.io/google_samples/gb-frontend:v3
```