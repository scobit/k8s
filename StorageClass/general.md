Default StorageClass is then used to dynamically provision storage for PersistentVolumeClaims that do not require any specific storage class. 

Deleting the default StorageClass may not work, as it may be re-created automatically by the addon manager running in your cluster. 
Please consult the docs for your installation for details about addon manager and how to disable individual addons.

Please note that at most one StorageClass can be marked as default. 
If two or more of them are marked as default, a PersistentVolumeClaim without storageClassName explicitly specified cannot be created.

The default StorageClass has an annotation storageclass.kubernetes.io/is-default-class set to true. 
Any other value or absence of the annotation is interpreted as false.

#### List the StorageClasses in your cluster:
kubectl get storageclass

#### To mark a StorageClass as non-default, you need to change its value to false:
kubectl patch storageclass StorageClassName -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"false"}}}'

#### Mark a StorageClass as default. Similar to the previous step, you need to add/set the annotation storageclass.kubernetes.io/is-default-class=true.
kubectl patch storageclass gold -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'

