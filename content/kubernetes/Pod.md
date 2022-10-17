---
title: "Pod"
date: 2021-02-24T17:43:39+09:00
draft: true
---


# Pod API

- pod.yaml 샘플코드


```
apiVersion: v1
kind: Pod
metadata:
  name: pod-example
spec:
  containers:
  - name: ubuntu
    image: ubuntu:trusty
    command: ["echo"]
    args: ["Hello World"]
```



| Field | Description |
| ----- | ----------- |
| `apiVersion`<br>*string* | APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: [https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#resources](https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#resources) |
| `kind`<br>*string* | Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: [https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#types-kinds](https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#types-kinds) |
| `metadata`<br>*[ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#objectmeta-v1-meta)* | Standard object's metadata. More info: [https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#metadata](https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#metadata) |
| `spec`<br>*[PodSpec](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#podspec-v1-core)* | Specification of the desired behavior of the pod. More info: [https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#spec-and-status](https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#spec-and-status) |
| `status`<br>*[PodStatus](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#podstatus-v1-core)* | Most recently observed status of the pod. This data may not be up to date. Populated by the system. Read-only. More info: [https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#spec-and-status](https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#spec-and-status) |


## 1. apiVersion 
 * api 문서 버전


## 2. kind 

 * Kind는 이 개체가 나타내는 REST 리소스를 나타내는 문자열 

 ## 3. metadata 

  * 표준 개체 메타 데이터로 ObjectMeta 참고

 ## 4. spec 
 *  원하는 배포 동작 사양	 PodSpec 참고

### 4.1 PodSpec 


| Field | Description |
| ----- | ----------- |
| `activeDeadlineSeconds`<br>*integer* | Optional duration in seconds the pod may be active on the node relative to StartTime before the system will actively try to mark it failed and kill associated containers. Value must be a positive integer. |
| `affinity`<br>*[Affinity](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#affinity-v1-core)* | If specified, the pod's scheduling constraints |
| `automountServiceAccountToken`<br>*boolean* | AutomountServiceAccountToken indicates whether a service account token should be automatically mounted. |
| `containers`<br>*[Container](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#container-v1-core) array*<br>**patch strategy**: *merge*<br>**patch merge key**: *name* | List of containers belonging to the pod. Containers cannot currently be added or removed. There must be at least one container in a Pod. Cannot be updated. |
| `dnsConfig`<br>*[PodDNSConfig](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#poddnsconfig-v1-core)* | Specifies the DNS parameters of a pod. Parameters specified here will be merged to the generated DNS configuration based on DNSPolicy. |
| `dnsPolicy`<br>*string* | Set DNS policy for the pod. Defaults to "ClusterFirst". Valid values are 'ClusterFirstWithHostNet', 'ClusterFirst', 'Default' or 'None'. DNS parameters given in DNSConfig will be merged with the policy selected with DNSPolicy. To have DNS options set along with hostNetwork, you have to specify DNS policy explicitly to 'ClusterFirstWithHostNet'. |
| `enableServiceLinks`<br>*boolean* | EnableServiceLinks indicates whether information about services should be injected into pod's environment variables, matching the syntax of Docker links. Optional: Defaults to true. |
| `ephemeralContainers`<br>*[EphemeralContainer](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#ephemeralcontainer-v1-core) array*<br>**patch strategy**: *merge*<br>**patch merge key**: *name* | List of ephemeral containers run in this pod. Ephemeral containers may be run in an existing pod to perform user-initiated actions such as debugging. This list cannot be specified when creating a pod, and it cannot be modified by updating the pod spec. In order to add an ephemeral container to an existing pod, use the pod's ephemeralcontainers subresource. This field is alpha-level and is only honored by servers that enable the EphemeralContainers feature. |
| `hostAliases`<br>*[HostAlias](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#hostalias-v1-core) array*<br>**patch strategy**: *merge*<br>**patch merge key**: *ip* | HostAliases is an optional list of hosts and IPs that will be injected into the pod's hosts file if specified. This is only valid for non-hostNetwork pods. |
| `hostIPC`<br>*boolean* | Use the host's ipc namespace. Optional: Default to false. |
| `hostNetwork`<br>*boolean* | Host networking requested for this pod. Use the host's network namespace. If this option is set, the ports that will be used must be specified. Default to false. |
| `hostPID`<br>*boolean* | Use the host's pid namespace. Optional: Default to false. |
| `hostname`<br>*string* | Specifies the hostname of the Pod If not specified, the pod's hostname will be set to a system-defined value. |
| `imagePullSecrets`<br>*[LocalObjectReference](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#localobjectreference-v1-core) array*<br>**patch strategy**: *merge*<br>**patch merge key**: *name* | ImagePullSecrets is an optional list of references to secrets in the same namespace to use for pulling any of the images used by this PodSpec. If specified, these secrets will be passed to individual puller implementations for them to use. For example, in the case of docker, only DockerConfig type secrets are honored. More info: [https://kubernetes.io/docs/concepts/containers/images#specifying-imagepullsecrets-on-a-pod](https://kubernetes.io/docs/concepts/containers/images#specifying-imagepullsecrets-on-a-pod) |
| `initContainers`<br>*[Container](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#container-v1-core) array*<br>**patch strategy**: *merge*<br>**patch merge key**: *name* | List of initialization containers belonging to the pod. Init containers are executed in order prior to containers being started. If any init container fails, the pod is considered to have failed and is handled according to its restartPolicy. The name for an init container or normal container must be unique among all containers. Init containers may not have Lifecycle actions, Readiness probes, Liveness probes, or Startup probes. The resourceRequirements of an init container are taken into account during scheduling by finding the highest request/limit for each resource type, and then using the max of of that value or the sum of the normal containers. Limits are applied to init containers in a similar fashion. Init containers cannot currently be added or removed. Cannot be updated. More info: [https://kubernetes.io/docs/concepts/workloads/pods/init-containers/](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/) |
| `nodeName`<br>*string* | NodeName is a request to schedule this pod onto a specific node. If it is non-empty, the scheduler simply schedules this pod onto that node, assuming that it fits resource requirements. |
| `nodeSelector`<br>*object* | NodeSelector is a selector which must be true for the pod to fit on a node. Selector which must match a node's labels for the pod to be scheduled on that node. More info: [https://kubernetes.io/docs/concepts/configuration/assign-pod-node/](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/) |
| `overhead`<br>*object* | Overhead represents the resource overhead associated with running a pod for a given RuntimeClass. This field will be autopopulated at admission time by the RuntimeClass admission controller. If the RuntimeClass admission controller is enabled, overhead must not be set in Pod create requests. The RuntimeClass admission controller will reject Pod create requests which have the overhead already set. If RuntimeClass is configured and selected in the PodSpec, Overhead will be set to the value defined in the corresponding RuntimeClass, otherwise it will remain unset and treated as zero. More info: [https://git.k8s.io/enhancements/keps/sig-node/20190226-pod-overhead.md](https://git.k8s.io/enhancements/keps/sig-node/20190226-pod-overhead.md) This field is alpha-level as of Kubernetes v1.16, and is only honored by servers that enable the PodOverhead feature. |
| `preemptionPolicy`<br>*string* | PreemptionPolicy is the Policy for preempting pods with lower priority. One of Never, PreemptLowerPriority. Defaults to PreemptLowerPriority if unset. This field is beta-level, gated by the NonPreemptingPriority feature-gate. |
| `priority`<br>*integer* | The priority value. Various system components use this field to find the priority of the pod. When Priority Admission Controller is enabled, it prevents users from setting this field. The admission controller populates this field from PriorityClassName. The higher the value, the higher the priority. |
| `priorityClassName`<br>*string* | If specified, indicates the pod's priority. "system-node-critical" and "system-cluster-critical" are two special keywords which indicate the highest priorities with the former being the highest priority. Any other name must be defined by creating a PriorityClass object with that name. If not specified, the pod priority will be default or zero if there is no default. |
| `readinessGates`<br>*[PodReadinessGate](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#podreadinessgate-v1-core) array* | If specified, all readiness gates will be evaluated for pod readiness. A pod is ready when all its containers are ready AND all conditions specified in the readiness gates have status equal to "True" More info: [https://git.k8s.io/enhancements/keps/sig-network/0007-pod-ready%2B%2B.md](https://git.k8s.io/enhancements/keps/sig-network/0007-pod-ready%2B%2B.md) |
| `restartPolicy`<br>*string* | Restart policy for all containers within the pod. One of Always, OnFailure, Never. Default to Always. More info: [https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/#restart-policy](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/#restart-policy) |
| `runtimeClassName`<br>*string* | RuntimeClassName refers to a RuntimeClass object in the node.k8s.io group, which should be used to run this pod. If no RuntimeClass resource matches the named class, the pod will not be run. If unset or empty, the "legacy" RuntimeClass will be used, which is an implicit class with an empty definition that uses the default runtime handler. More info: [https://git.k8s.io/enhancements/keps/sig-node/runtime-class.md](https://git.k8s.io/enhancements/keps/sig-node/runtime-class.md) This is a beta feature as of Kubernetes v1.14. |
| `schedulerName`<br>*string* | If specified, the pod will be dispatched by specified scheduler. If not specified, the pod will be dispatched by default scheduler. |
| `securityContext`<br>*[PodSecurityContext](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#podsecuritycontext-v1-core)* | SecurityContext holds pod-level security attributes and common container settings. Optional: Defaults to empty. See type description for default values of each field. |
| `serviceAccount`<br>*string* | DeprecatedServiceAccount is a depreciated alias for ServiceAccountName. Deprecated: Use serviceAccountName instead. |
| `serviceAccountName`<br>*string* | ServiceAccountName is the name of the ServiceAccount to use to run this pod. More info: [https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/) |
| `setHostnameAsFQDN`<br>*boolean* | If true the pod's hostname will be configured as the pod's FQDN, rather than the leaf name (the default). In Linux containers, this means setting the FQDN in the hostname field of the kernel (the nodename field of struct utsname). In Windows containers, this means setting the registry value of hostname for the registry key HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters to FQDN. If a pod does not have FQDN, this has no effect. Default to false. |
| `shareProcessNamespace`<br>*boolean* | Share a single process namespace between all of the containers in a pod. When this is set containers will be able to view and signal processes from other containers in the same pod, and the first process in each container will not be assigned PID 1. HostPID and ShareProcessNamespace cannot both be set. Optional: Default to false. |
| `subdomain`<br>*string* | If specified, the fully qualified Pod hostname will be "\<hostname>.\<subdomain>.\<pod namespace>.svc.\<cluster domain>". If not specified, the pod will not have a domainname at all. |
| `terminationGracePeriodSeconds`<br>*integer* | Optional duration in seconds the pod needs to terminate gracefully. May be decreased in delete request. Value must be non-negative integer. The value zero indicates delete immediately. If this value is nil, the default grace period will be used instead. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. Defaults to 30 seconds. |
| `tolerations`<br>*[Toleration](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#toleration-v1-core) array* | If specified, the pod's tolerations. |
| `topologySpreadConstraints`<br>*[TopologySpreadConstraint](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#topologyspreadconstraint-v1-core) array*<br>**patch strategy**: *merge*<br>**patch merge key**: *topologyKey* | TopologySpreadConstraints describes how a group of pods ought to spread across topology domains. Scheduler will schedule pods in a way which abides by the constraints. All topologySpreadConstraints are ANDed. |
| `volumes`<br>*[Volume](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#volume-v1-core) array*<br>**patch strategy**: *merge,retainKeys*<br>**patch merge key**: *name* | List of volumes that can be mounted by containers belonging to the pod. More info: [https://kubernetes.io/docs/concepts/storage/volumes](https://kubernetes.io/docs/concepts/storage/volumes) | 


 
 #### 4.1.1 Container 

 | Field | Description |
| ----- | ----------- |
| `args`<br>*string array* | Arguments to the entrypoint. The docker image's CMD is used if this is not provided. Variable references $(VAR\_NAME) are expanded using the container's environment. If a variable cannot be resolved, the reference in the input string will be unchanged. The $(VAR\_NAME) syntax can be escaped with a double $$, ie: $$(VAR\_NAME). Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: [https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell](https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell) |
| `command`<br>*string array* | Entrypoint array. Not executed within a shell. The docker image's ENTRYPOINT is used if this is not provided. Variable references $(VAR\_NAME) are expanded using the container's environment. If a variable cannot be resolved, the reference in the input string will be unchanged. The $(VAR\_NAME) syntax can be escaped with a double $$, ie: $$(VAR\_NAME). Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: [https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell](https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell) |
| `env`<br>*[EnvVar](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#envvar-v1-core) array*<br>**patch strategy**: *merge*<br>**patch merge key**: *name* | List of environment variables to set in the container. Cannot be updated. |
| `envFrom`<br>*[EnvFromSource](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#envfromsource-v1-core) array* | List of sources to populate environment variables in the container. The keys defined within a source must be a C\_IDENTIFIER. All invalid keys will be reported as an event when the container is starting. When a key exists in multiple sources, the value associated with the last source will take precedence. Values defined by an Env with a duplicate key will take precedence. Cannot be updated. |
| `image`<br>*string* | Docker image name. More info: [https://kubernetes.io/docs/concepts/containers/images](https://kubernetes.io/docs/concepts/containers/images) This field is optional to allow higher level config management to default or override container images in workload controllers like Deployments and StatefulSets. |
| `imagePullPolicy`<br>*string* | Image pull policy. One of Always, Never, IfNotPresent. Defaults to Always if :latest tag is specified, or IfNotPresent otherwise. Cannot be updated. More info: [https://kubernetes.io/docs/concepts/containers/images#updating-images](https://kubernetes.io/docs/concepts/containers/images#updating-images) |
| `name`<br>*string* | Name of the container specified as a DNS\_LABEL. Each container in a pod must have a unique name (DNS\_LABEL). Cannot be updated. |
| `ports`<br>*[ContainerPort](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#containerport-v1-core) array*<br>**patch strategy**: *merge*<br>**patch merge key**: *containerPort* | List of ports to expose from the container. Exposing a port here gives the system additional information about the network connections a container uses, but is primarily informational. Not specifying a port here DOES NOT prevent that port from being exposed. Any port which is listening on the default "0.0.0.0" address inside a container will be accessible from the network. Cannot be updated. |
| `readinessProbe`<br>*[Probe](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#probe-v1-core)* | Periodic probe of container service readiness. Container will be removed from service endpoints if the probe fails. Cannot be updated. More info: [https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes) |
| `resources`<br>*[ResourceRequirements](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#resourcerequirements-v1-core)* | Compute Resources required by this container. Cannot be updated. More info: [https://kubernetes.io/docs/concepts/configuration/manage-compute-resources-container/](https://kubernetes.io/docs/concepts/configuration/manage-compute-resources-container/) |
| `terminationMessagePath`<br>*string* | Optional: Path at which the file to which the container's termination message will be written is mounted into the container's filesystem. Message written is intended to be brief final status, such as an assertion failure message. Will be truncated by the node if greater than 4096 bytes. The total message length across all containers will be limited to 12kb. Defaults to /dev/termination-log. Cannot be updated. |
| `volumeMounts`<br>*[VolumeMount](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#volumemount-v1-core) array*<br>**patch strategy**: *merge*<br>**patch merge key**: *mountPath* | Pod volumes to mount into the container's filesystem. Cannot be updated. |
| `workingDir`<br>*string* | Container's working directory. If not specified, the container runtime's default will be used, which might be configured in the container image. Cannot be updated. |