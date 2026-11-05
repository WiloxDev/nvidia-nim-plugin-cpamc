<p align="center">
  <img src="assets/logo.png" alt="NVIDIA NIM Plugin for CPAMC" width="220" />
</p>

# ⚡ NVIDIA NIM Plugin for CLI PROXY API CONSOLE (CPAMC)

[![Gentle Hub](https://img.shields.io/badge/Gentle%20Hub-Plugin-F095C8?style=for-the-badge)](https://gentlemanprogramming.com/gentle-hub/)
[![Ecosistema](https://img.shields.io/badge/Ecosistema-CPAMC%20%7C%20Gentle--Shell-green?style=for-the-badge)](#)
[![Discord](https://img.shields.io/badge/Discord-Apoyo-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://bit.ly/48zTJUo)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

Plugin oficial de alto rendimiento en Go (C-ABI) que integra el catálogo de microservicios de inferencia acelerada de **NVIDIA NIM** (National Institute of Standards / NVIDIA Inception) en **CLI PROXY API CONSOLE (CPAMC)** y **Gentle-Shell**.

Permite acceder a modelos de frontera (DeepSeek R1, Llama 3.1 405B, Nemotron 70B, Qwen) alojados en la infraestructura acelerada de NVIDIA, con créditos iniciales gratuitos para desarrolladores.

> 💬 **Comunidad y Soporte Oficial:** `wilox2` · [Servidor de Discord](https://bit.ly/48zTJUo)

---

## 🌟 Modelos Principales Disponibles

| ID del Modelo en NIM | Nombre en Gentle Shell | Contexto | Enfoque |
| :--- | :--- | :---: | :--- |
| `deepseek-ai/deepseek-r1` | DeepSeek R1 (NVIDIA NIM) | 128k | Razonamiento puro acelerado por TensorRT-LLM. |
| `meta/llama-3.1-405b-instruct` | Llama 3.1 405B (NVIDIA NIM) | 128k | El modelo de pesos abiertos más grande y potente. |
| `meta/llama-3.3-70b-instruct` | Llama 3.3 70B (NVIDIA NIM) | 128k | Rendimiento excepcional con baja latencia para codificación diaria. |
| `nvidia/llama-3.1-nemotron-70b-instruct` | Nemotron 70B (NVIDIA NIM) | 128k | Ajustado por NVIDIA para máxima fidelidad en respuestas complejas. |

---

## 🔑 Cómo Obtener tu API Key Gratuita de NVIDIA NIM

1. Ve al portal oficial de NVIDIA: 👉 **[build.nvidia.com](https://build.nvidia.com)**
2. Inicia sesión o regístrate con tu cuenta de desarrollador.
3. Al crear tu cuenta recibirás **1,000 créditos gratuitos** para probar la inferencia acelerada en la nube.
4. Genera tu clave en el panel de control (`nvapi-...`).

---

## 🛠️ Métodos de Instalación

### Método 1: Compilación local con Go
Requiere Go (>= 1.22) y `gcc`/`clang`:
```bash
git clone https://github.com/WiloxDev/nvidia-nim-plugin-cpamc.git
cd nvidia-nim-plugin-cpamc
make install
```
El binario `nvidia-nim-plugin-linux-amd64.so` se copiará en la carpeta de plugins de CPAMC (`~/services/cliproxy/plugins/`).

---

### Método 2: Despliegue en Docker
Monta el archivo `.so` en el contenedor de CPAMC:
```yaml
services:
  cpamc:
    image: ghcr.io/router-for-me/cliproxyapi:latest
    volumes:
      - ./plugins/nvidia-nim-plugin-linux-amd64.so:/app/plugins/nvidia-nim.so:ro
      - ./config.yaml:/app/config.yaml:ro
    ports:
      - "8317:8317"
```

---

## ⚙️ Configuración en CPAMC

### En la Consola Web Oficial
1. Abre: 👉 **[http://127.0.0.1:8317/management.html](http://127.0.0.1:8317/management.html)**
2. Entra a **Plugins / NVIDIA NIM**.
3. Pega tu API Key de NVIDIA (`nvapi-...`).

### En `config.yaml`
```yaml
plugins:
  nvidia_nim:
    enabled: true
    api_key: "nvapi-tu-clave-de-nvidia"
    base_url: "https://integrate.api.nvidia.com/v1"
```

---

## 🚀 Uso en Gentle Shell

1. Sincroniza los modelos con `/cpamc refresh`.
2. Escribe `/model` y elige tu modelo de NVIDIA NIM (ej: `cpamc/meta/llama-3.1-405b-instruct`).
3. *(Opcional)* Si cuentas con múltiples claves de NVIDIA NIM, utiliza **[CPAMC Auto Switcher Pro](https://github.com/WiloxDev/cpamc-auto-switcher-pro)** para rotar automáticamente entre cuentas cuando se agoten los créditos de una clave.

---

## 🌐 Ecosistema de la Suite WiloxDev para Gentle Hub

- 🌉 **[bridge-cpamc-oficial](https://github.com/WiloxDev/bridge-cpamc-oficial)** — Puente e instalador oficial multiplataforma de CPAMC.
- ⚡ **[cpamc-auto-switcher-pro](https://github.com/WiloxDev/cpamc-auto-switcher-pro)** — Balanceador de carga y conmutación automática anti-429.
- 🐋 **[deepseek-plugin-cpamc](https://github.com/WiloxDev/deepseek-plugin-cpamc)** — Plugin oficial de DeepSeek V3 y R1.
- 👁️ **[gentle-context-lens](https://github.com/WiloxDev/gentle-context-lens)** — Cabina de contexto, semáforo de tokens y poda quirúrgica.
- 🤖 **[gentle-claude-bridge](https://github.com/WiloxDev/gentle-claude-bridge)** — Conexión a Claude Code Pro/Max sin API keys por token.

---

## 📄 Licencia

MIT © Wilox. Desarrollado para la comunidad de Gentle Shell y CLIProxyAPI.
