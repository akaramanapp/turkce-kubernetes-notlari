## Kubernetes (k8s) Nedir?

Kubernetes (k8s) açık kaynak olarak geliştirlen bir container orkestrasyon platformudur. Başlıca özelliklerinin arasında uygulamaların dağıtımı, ölçeklenmesi ve yönetilmesi bulunmaktadır. 

## Pods
Kubernetes üzerinde çalışan her bir prosesi temsil etmektedir. Genel kabul görmüş kullanım şekli herbir pod üzerinde bir container çalıştırılmasıdır. Tabiki bunun istisna olduğu durumlar da mevcuttur.

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
