# Estoque Auto UDI — App de gestão e catálogo de estoque automotivo

App Android (gerado via Capacitor) para gestão de estoque de veículos, com foco no pátio de
Uberlândia. Funciona 100% offline, salvando os dados no próprio celular (IndexedDB).

## O que já está pronto neste projeto
- `www/index.html` — o aplicativo completo (importação de CSV, grade 3 colunas, fotos,
  conferência física, modo cliente/gestão, cópia de ficha para WhatsApp etc).
- `capacitor.config.json` e `package.json` — configuração do Capacitor.
- `.github/workflows/build-apk.yml` — workflow que compila o `app-debug.apk`
  automaticamente a cada push, usando o GitHub Actions (não precisa de computador
  com Android Studio).

## Passo a passo para gerar o .apk (sem precisar instalar nada no seu PC)

1. **Crie uma conta gratuita no GitHub** (se ainda não tiver): https://github.com/signup
2. **Crie um repositório novo**, por exemplo `estoque-auto-udi` (pode ser privado).
3. **Envie estes arquivos para o repositório.** Duas formas:
   - *Mais fácil (pelo navegador):* na página do repositório, clique em
     **"Add file" → "Upload files"**, arraste a pasta/arquivos deste projeto
     (mantendo a estrutura de pastas) e clique em **"Commit changes"**.
   - *Via linha de comando:*
     ```
     git init
     git add .
     git commit -m "App estoque automotivo"
     git branch -M main
     git remote add origin https://github.com/SEU-USUARIO/estoque-auto-udi.git
     git push -u origin main
     ```
4. Assim que o push for feito, o GitHub já começa a compilar sozinho. Para acompanhar:
   - Vá até a aba **"Actions"** no topo do repositório.
   - Clique no workflow mais recente ("Build Android APK") — ele leva de 3 a 6 minutos.
5. **Quando o ícone ficar verde (✓)**, role a página até **"Artifacts"** (parte de baixo
   da execução) e clique em **`app-debug-apk`** para baixar um `.zip`.
6. **Extraia o .zip no seu celular** (ou no PC e depois transfira o `app-debug.apk`
   para o celular por cabo, WhatsApp Web, Google Drive, e-mail etc).

## Como instalar o .apk no Android

1. Abra o arquivo `app-debug.apk` no celular (pelo Gerenciador de Arquivos, Drive, etc).
2. O Android vai avisar que é "app de fonte desconhecida" — toque em
   **"Configurações"** no próprio aviso e ative **"Permitir desta fonte"**.
3. Volte e toque em **"Instalar"**.
4. Pronto! O ícone **"Estoque Auto UDI"** aparece na tela do celular.

> Isso só é necessário porque é um app de testes (debug), feito sob medida para você —
> não precisa passar pela Play Store.

## Como usar o app
- **Importar CSV**: botão "⬆️ Importar CSV" no topo. Baixe o modelo pelo botão
  "⬇️ Modelo CSV" se quiser ver o formato exato
  (`reserva;modelo;placa;ano;km;cor;tabela;marca;empresa;patio;dpt`).
- A importação sempre prioriza carros de **Uberlândia** por padrão — toque em
  **"📍 UDI"** para ver todos os pátios.
- Toque em um carro para abrir a ficha completa (fotos, valores, observações).
- O ícone **👁️ / 🙈** no topo alterna entre **Modo Gestão** (mostra custo/margem) e
  **Modo Cliente** (oculta tudo isso).
- Dentro da ficha, use **"📋 Copiar p/ WhatsApp"** para copiar um texto de divulgação
  sem custo nem margem, pronto para colar numa conversa.
- O botão redondo no canto do card confirma a **conferência física** do carro no pátio.

## Atualizando o app depois
Sempre que você editar `www/index.html` (ou qualquer arquivo) e enviar (`git push`)
para o GitHub, um novo `.apk` é gerado automaticamente na aba **Actions**. É só repetir
os passos 4 a 6 acima para baixar a nova versão.

## Rodando/testando no computador antes de gerar o APK (opcional)
Basta abrir o arquivo `www/index.html` em qualquer navegador — o app inteiro funciona
também no navegador, já que foi feito em HTML/JS puro com armazenamento local.
