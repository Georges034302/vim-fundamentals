# Exercise 8 – Advanced DevOps Vim Lab: Incident Patch + Sanitisation (Capstone)

**Difficulty:** Advanced  
**Time target:** 45–75 minutes  
**Allowed modes:** Normal + Insert  
**Not allowed:** Visual mode, macros, plugins  
**Files:** `.env`, `config/nginx.conf`, `k8s/deployment.yaml`

---

## Objective

You will simulate a real DevOps incident hotfix by:

- Editing **multiple files in one Vim session**
- Fixing a **port mismatch** consistently across configs
- Correcting a Kubernetes readiness probe path
- Updating an internal service URL
- Sanitising secrets in `.env` (targeted change only)
- Proving correctness using searches **inside Vim**
- Saving clean, auditable changes

---

## Part 0 — Create the DevOps files (Setup)

Run these commands in a terminal **exactly**:

### 0.1 Create folders

```bash
mkdir -p config k8s
```

### 0.2 Create `.env`

```bash
cat > .env << 'EOF'
APP_NAME=student-app
APP_ENV=prod
PORT=5000
API_BASE_URL=http://localhost:5000
DB_PASSWORD=superSecret99
JWT_SECRET=myjwtsecret84
LOG_LEVEL=debug
EOF
```

### 0.3 Create `config/nginx.conf`

```bash
cat > config/nginx.conf << 'EOF'
server {
  listen 80;
  server_name _;

  location /api/ {
    proxy_pass http://127.0.0.1:8080/;
    proxy_set_header Host $host;
  }

  location /health {
    return 200 "OK";
  }
}
EOF
```

### 0.4 Create `k8s/deployment.yaml`

```bash
cat > k8s/deployment.yaml << 'EOF'
apiVersion: apps/v1
kind: Deployment
metadata:
  name: student-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: student-app
  template:
    metadata:
      labels:
        app: student-app
    spec:
      containers:
      - name: student-app
        image: student-app:latest
        ports:
        - containerPort: 8080
        env:
        - name: PORT
          value: "8080"
        - name: API_BASE_URL
          value: "http://localhost:8080"
        - name: LOG_LEVEL
          value: "debug"
        readinessProbe:
          httpGet:
            path: /status
            port: 8080
          initialDelaySeconds: 2
          periodSeconds: 5
EOF
```

---

## Part 1 — Student Tasks

### Task 1 — Open all files in one Vim session

Open the three files in one Vim session (any valid method is allowed).

**Requirement:** You must be able to switch between files without closing Vim.

---

### Task 2 — Fix the port mismatch end-to-end

The system must use port **5000** consistently.

Update all occurrences of `8080` to `5000` in:

- `config/nginx.conf` (backend in `proxy_pass`)
- `k8s/deployment.yaml` (`containerPort`, `env PORT`, probe port)
- Keep `.env` as `PORT=5000` (already correct)

---

### Task 3 — Fix readiness probe path

Change Kubernetes readiness path from:

- `/status` → `/health`

---

### Task 4 — Update k8s API_BASE_URL

In `k8s/deployment.yaml`, set:

- `API_BASE_URL` → `http://student-app:5000`

Constraint: do not leave `localhost` in the Kubernetes file.

---

### Task 5 — Sanitise secrets in `.env` (targeted)

Only for these keys:

- `DB_PASSWORD`
- `JWT_SECRET`

Replace the **two digits at the end** of each value with `##`:

- `superSecret99` → `superSecret##`
- `myjwtsecret84` → `myjwtsecret##`

Constraint: do not modify other lines.

---

### Task 6 — Add a verification note

Append this line at the end of `.env`:

```text
VERIFIED: no 8080 remains; ports aligned to 5000; secrets sanitized
```

---

### Task 7 — Verification inside Vim

Without leaving Vim, prove all are true:

- No `8080` exists in any file
- Readiness path is `/health`
- `API_BASE_URL` in k8s is `http://student-app:5000`
- `.env` secrets are sanitised (end digits replaced with `##`)

---

### Task 8 — Save and exit

Save all files and quit.

---

# Solution (Strict, Assumption-Free)

## Step 1 — Open all files in one Vim session

Run:

```bash
vim .env config/nginx.conf k8s/deployment.yaml
```

---

## Step 2 — Switch between files (proof you can multi-file)

In Vim (Normal mode), use these commands:

Go to next file:
```vim
:next
```

Go to previous file:
```vim
:prev
```

---

## Step 3 — Fix Nginx backend port (8080 → 5000)

1) Go to `config/nginx.conf`:

```vim
:edit config/nginx.conf
```

2) Replace all `8080` with `5000` in this file:

```vim
:%s/8080/5000/g
```

3) Save this file:

```vim
:w
```

---

## Step 4 — Fix Kubernetes ports and probe port (8080 → 5000)

1) Go to `k8s/deployment.yaml`:

```vim
:edit k8s/deployment.yaml
```

2) Replace all `8080` with `5000` in this file:

```vim
:%s/8080/5000/g
```

3) Fix readiness path `/status` → `/health`:

```vim
:%s#/status#/health#g
```

4) Replace k8s API base URL value with the required service URL:

Search for the line containing `API_BASE_URL`:

```vim
/API_BASE_URL
```

Move to the line containing the value (if needed press `j` once), then replace the entire URL string on that line using substitute:

```vim
:s#http://localhost:5000#http://student-app:5000#
```

5) Save this file:

```vim
:w
```

---

## Step 5 — Sanitise `.env` secrets (targeted edits only)

1) Go to `.env`:

```vim
:edit .env
```

2) Replace `DB_PASSWORD` ending digits with `##`:

Search for `DB_PASSWORD` line:

```vim
/DB_PASSWORD=
```

Change the value by replacing the final two digits:

```vim
:s/99/##/
```

3) Replace `JWT_SECRET` ending digits with `##`:

Search for `JWT_SECRET` line:

```vim
/JWT_SECRET=
```

Replace the final two digits:

```vim
:s/84/##/
```

4) Append the verification note at end of file:

Go to last line:

```vim
G
```

Open a new line below and enter Insert mode:

```vim
o
```

Type:

```text
VERIFIED: no 8080 remains; ports aligned to 5000; secrets sanitized
```

Return to Normal mode:

```vim
Esc
```

5) Save `.env`:

```vim
:w
```

---

## Step 6 — Verification inside Vim (must be true)

### 6.1 Confirm no `8080` remains anywhere

Search for `8080`:

```vim
/8080
```

**Correct result:** Vim reports **Pattern not found**.

Repeat once per file if you want to be explicit:

```vim
:edit config/nginx.conf
/8080
:edit k8s/deployment.yaml
/8080
:edit .env
/8080
```

### 6.2 Confirm readiness path is `/health` in k8s

```vim
:edit k8s/deployment.yaml
/health
```

### 6.3 Confirm k8s API_BASE_URL is correct

```vim
/API_BASE_URL
```

**Correct value must be present on that line:**

```text
http://student-app:5000
```

### 6.4 Confirm `.env` secrets are sanitised

```vim
:edit .env
/DB_PASSWORD=
/JWT_SECRET=
```

**Correct values must be:**

```text
DB_PASSWORD=superSecret##
JWT_SECRET=myjwtsecret##
```

---

## Step 7 — Save all and exit

If any file is still unsaved, save all:

```vim
:wall
```

Quit:

```vim
:q
```

If Vim refuses to quit due to unsaved changes, use:

```vim
:wq
```

---

## Completion Checklist (Pass/Fail)

PASS if all are true:

- `config/nginx.conf` uses port `5000` in `proxy_pass`
- `k8s/deployment.yaml` uses port `5000` everywhere (containerPort, env PORT, probe port)
- readiness probe path is `/health`
- k8s `API_BASE_URL` is `http://student-app:5000`
- `.env` secrets are:
  - `DB_PASSWORD=superSecret##`
  - `JWT_SECRET=myjwtsecret##`
- `.env` contains the verification note line
- Searching for `/8080` returns **Pattern not found**
