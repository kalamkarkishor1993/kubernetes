# Copilot Instructions for kubernetes repo

## 1) Big picture
- This repo stores Kubernetes manifest examples (Pod, Service, ReplicationController, ReplicaSet, Deployment). Files are:
  - `pod.yaml`, `deployment.yaml`, `rc.yaml`, `rs.yaml`, `rss.yaml`
- Goal: show basic K8s resource patterns and label-selection flow.
- Cloud actor: user likely applies with `kubectl apply -f .` or specific file.

## 2) What to edit
- Keep standard Kubernetes schema keys: `apiVersion`, `kind`, `metadata`, `spec`.
- `rss.yaml` is the most complete valid model:
  - `apiVersion: apps/v1`, `kind: ReplicaSet`, `selector.matchLabels`, `template.spec.containers`.
- `rc.yaml` and `rs.yaml` contain intentional/incomplete examples and should be normalized before applying.
- `deployment.yaml` has typos (`app/v1` with `kind: Deployement`, list style on metadata) - follow K8s fields.

## 3) Project-specific conventions
- labels are mostly `app: netflix`, `env: dev`, `app: nginx`.
- Service selector in `pod.yaml` uses `env: dev`; match these exactly.
- There is no Helm or Kustomize here: raw manifests only.

## 4) Developer flow
- Validate before apply:
  - `kubectl apply --dry-run=client -f <file>`
  - `kubectl apply --dry-run=client -f .` for full repo
- Inspect generated objects:
  - `kubectl get all -l env=dev` or `kubectl describe rs/nginx-replicaset`.
- For errors, fix YAML formatting and wrong keys. e.g. `matchLabes` → `matchLabels`, `kind:` missing in `rs.yaml` blocks.

## 5) Integration / communication patterns
- `pod.yaml` includes `Service` + `Pod` in one file; the `Service` selects by label, not by pod name.
- `rs.yaml` intended to show selector examples (`matchLabels`, `matchExpression` with operators `In`, `NotIn`, `Exists`).
- `rc.yaml` and `rss.yaml` represent two controller types (RC vs. RS) with selectors tied to template labels.

## 6) Debug hints for AI coder
- If user asks to add new workload, follow existing pattern in `rss.yaml` exactly:
  - same apiVersion/group, selector + template label parity.
- Keep resources idempotent and non-conflicting names (`nginx-replicaset`, `svc-first-pod`).
- Avoid introducing extra fields not present in these examples.

## 7) No code tests present
- No build/test automation detected in repository (no `Makefile`, `CI`, `Dockerfile`).
- Agent should suggest adding schema validation step if asked.

---

> Feedback requested: Tell me if any section is unclear or if you want a “quick-start apply” block added for the exact cluster environment you are using.