(
  count (
    (kube_pod_container_resource_requests_memory_bytes{namespace=~".*"})
    and
    (predict_linear(kube_pod_container_resource_requests_memory_bytes{namespace=~".*"}[1d], 5 * 24 * 60 * 60) < 0)
  )
)
or
vector(0)
