## 1. Ramas según el entorno

| Rama                | Para qué sirve                              | Quién trabaja |
| ------------------- | ------------------------------------------- | ------------- |
| `main` (o `master`) | **Producción** (lo que ve el usuario final) | Prod          |
| `qa`                | Validación y testing                        | QA            |
| `dev`               | Desarrollo activo                           | Devs          |
| `feature/*`         | Funcionalidades nuevas                      | Devs          |

---

## 2. Estructura de ramas

```text
main        ← (protegida) - Solo despliegues a producción
  ↑
qa          ← Testing / QA
  ↑
dev         ← Integración continua front+back
  ↑
feature/login
feature/carrito
```

---

## 3. Creando ramas

### 🔹 1. Crear rama `dev` desde `main`

```bash
git checkout -b dev
git push -u origin dev
```

---

### 🔹 2. Crear rama `qa` desde `dev`

```bash
git checkout -b qa
git push -u origin qa
```

---

## 3️⃣ Flujo de trabajo básico

### 🔸 Paso 1: Crear una rama de feature desde dev

```bash
git checkout dev
git pull origin dev
git checkout -b feature/front-login   # frontend
git checkout -b feature/back-auth     # backend
```

Trabajar en carpetas separadas:
frontend/      # Frontend developer trabaja aquí
backend/       # Backend developer trabaja aquí


### 🔸 Paso 2: Programar y commitear

Commits pequeños y claros:

```bash
git add .
git commit -m "feat(front): login de usuario"
git push -u origin feature/front-login
```

---

### 🔸 Paso 3: Pull Request a `dev`

En GitHub:

* **feature/front-login → dev**
* Otro dev revisa
* Se hace **merge**

👉 Cuando se mergea, la feature ya está en `dev`.

---

## 5️⃣ Pasar a QA

Cuando `dev` está estable:

### 🔹 Pull Request

```
dev → qa
```

QA prueba todo en la rama `qa`.

Si hay bugs:

* Se corrigen en **nuevas ramas feature**
* Se vuelve a pasar por `dev` → `qa`

---

## 6️⃣ Pasar a Producción

Cuando QA aprueba:

### 🔹 Pull Request

```
qa → main
```

🚀 Eso es el **deploy a producción**.

---

## 7️⃣ Reglas importantes

❌ Nunca:

* Hacer commits directos en `main`
* Hacer commits directos en `qa`
* Hacer commits directos en `dev`

✅ Siempre:

* Usar ramas `feature/*`
* Usar Pull Requests
* Hacer `git pull` antes de empezar

---

## 8️⃣ Convención de nombres recomendada

```text
feature/front-login
feature/back-register-user
```
