(
  count (
    (kube_pod_container_resource_requests_cpu_cores{namespace=~".*"})
    and
    (predict_linear(kube_pod_container_resource_requests_cpu_cores{namespace=~".*"}[1d], 5 * 24 * 60 * 60) < 0)
  )
)   
or
vector(0)

