# 📝 Roteiro: Instalar e Configurar o File Browser no Windows 11

## ✅ 1. Baixar o File Browser

1. Acesse o site oficial do projeto:  
   [https://filebrowser.org/installation](https://filebrowser.org/installation)

2. Clique em **"Releases"** ou vá direto para:  
   [https://github.com/filebrowser/filebrowser/releases](https://github.com/filebrowser/filebrowser/releases)

3. Baixe o executável compatível com o seu sistema:  
   Exemplo: `windows-amd64-filebrowser.exe`

4. Renomeie o arquivo para `filebrowser.exe` (opcional).

5. Mova o executável para uma pasta permanente, como `C:\filebrowser\`.

---

## ✅ 2. Criar uma pasta de arquivos a serem compartilhados

1. Crie uma pasta para os arquivos:  
   Ex: `C:\filebrowser\arquivos`

---

## ✅ 3. Executar o File Browser

1. Abra o **Prompt de Comando (CMD)** como Administrador.

2. Navegue até a pasta do `filebrowser.exe`:
   ```cmd
   cd C:\filebrowser
   ```

3. Inicie o File Browser:
   ```cmd
   filebrowser.exe -r "C:\filebrowser\arquivos" --port 8080
   ```

   Explicação:
   - `-r` define o diretório raiz.
   - `--port 8080` define a porta.

---

## ✅ 4. Acessar o File Browser via navegador

1. No navegador do Windows, acesse:  
   `http://localhost:8080`

2. Login padrão:
   - Usuário: `admin`
   - Senha: `admin`

3. Altere a senha após o primeiro login.

---

## ✅ 5. Liberar a porta no firewall do Windows

1. Abra **"Firewall do Windows com segurança avançada"**.

2. Vá em **"Regras de Entrada" > "Nova Regra..."**

3. Escolha **Porta**, clique em Avançar.

4. Selecione **TCP**, insira `8080`, clique em Avançar.

5. Selecione **Permitir conexão**, clique em Avançar.

6. Marque todas as opções, clique em Avançar.

7. Nomeie como `File Browser`, clique em Concluir.

---

## ✅ 6. Acessar de outro dispositivo na rede local

1. Descubra o IP do notebook com:
   ```cmd
   ipconfig
   ```

2. Anote o **Endereço IPv4** (ex: `192.168.0.105`).

3. Em outro dispositivo, acesse:  
   `http://192.168.0.105:8080`

---

## ✅ 7. (Opcional) Criar atalho para iniciar automaticamente

1. Crie um atalho com:
   ```
   "C:\filebrowser\filebrowser.exe" -r "C:\filebrowser\arquivos" --port 8080
   ```

2. Pressione `Win + R`, digite `shell:startup` e cole o atalho lá.

---

## 🔐 Dica Extra: Permissões

Garanta permissões de leitura/gravação na pasta `C:\filebrowser\arquivos`.
