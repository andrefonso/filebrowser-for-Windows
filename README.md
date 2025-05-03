# 🗂️ Instalação e Configuração do File Browser no Windows 11 (atualizado)

Este roteiro ensina como instalar e configurar o [File Browser](https://filebrowser.org) no Windows 11 para compartilhar uma pasta com outros dispositivos da sua rede local.

---

## ✅ 1. Download e Instalação

1. Baixe e instale o File Browser via PowerShell (como Administrador):

```powershell
iwr -useb https://raw.githubusercontent.com/filebrowser/get/master/get.ps1 | iex
```

2. Mova o executável para um local definitivo, como:

```
C:\Program Files\filebrowser
```

3. Crie a pasta que você deseja compartilhar (exemplo):

```
C:\filebrowser\compartilhado
```

---

## ⚙️ 2. Primeiro teste manual

Abra o PowerShell **como Administrador** e execute:

```powershell
Start-Process 'C:\Program Files\filebrowser\filebrowser.exe' `
  -ArgumentList '-r C:\filebrowser\compartilhado --port 8080 --address 0.0.0.0' `
  -WorkingDirectory 'C:\Program Files\filebrowser'
```

Acesse de outro computador pela rede:

```
http://IP_DO_PC:8080/
```

---

## 🔥 3. Configurar o firewall do ESET

1. Abra o ESET Internet Security.
2. Vá em **Configuração Avançada > Rede > Proteção de Rede > Regras de Firewall**.
3. Crie uma nova regra:
   - **Nome**: Liberar File Browser
   - **Direção**: Ambos
   - **Ação**: Permitir
   - **Protocolo**: TCP
   - **Porta local**: 8080

---

## 🔄 4. Iniciar o File Browser automaticamente

### Opção 1: Usar um script `.bat` na inicialização

1. Crie um arquivo `iniciar_filebrowser.bat` com o conteúdo:

```bat
@echo off
start "" powershell -ExecutionPolicy Bypass -WindowStyle Hidden -Command "Start-Process 'C:\Program Files\filebrowser\filebrowser.exe' -ArgumentList '-r C:\filebrowser\compartilhado --port 8080 --address 0.0.0.0' -WorkingDirectory 'C:\Program Files\filebrowser'"
```

2. Coloque esse `.bat` na pasta de inicialização do Windows (pressione `Win + R` e digite):

```
shell:startup
```

### Opção 2 (avançado): Usar o Agendador de Tarefas

1. Abra o **Agendador de Tarefas**.
2. Crie uma nova tarefa:
   - Executar com privilégios elevados.
   - Acionar ao iniciar o computador.
   - Ação: iniciar um programa:
     - Programa: `powershell.exe`
     - Argumentos:

```powershell
-ExecutionPolicy Bypass -WindowStyle Hidden -Command "Start-Process 'C:\Program Files\filebrowser\filebrowser.exe' -ArgumentList '-r C:\filebrowser\compartilhado --port 8080 --address 0.0.0.0' -WorkingDirectory 'C:\Program Files\filebrowser'"
```

---

## ✅ Pronto!

Agora o File Browser iniciará automaticamente e poderá ser acessado pela rede local sempre que o computador for ligado.

**URL de acesso a partir de outro dispositivo:**
```
http://IP_DO_COMPUTADOR:8080/
```

Usuário padrão: `admin`  
Senha padrão: `admin`
