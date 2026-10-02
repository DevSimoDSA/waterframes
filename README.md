# 📺 WaterFrames 2.1.23 `configfix` — Guia de Multiplayer

Este é um fork do mod [SrRapero720/waterframes](https://github.com/SrRapero720/waterframes) para **Minecraft 1.21.1 / NeoForge**. 

Esta versão personalizada (`configfix`) traz uma correção fundamental para quem joga em servidores (Multiplayer), evitando crashes no cliente relacionados à leitura prematura das configurações do mod.

## 📋 Requisitos

Para que o mod funcione perfeitamente, você precisará das seguintes versões:

| Dependência | Versão Exigida | Onde Instalar |
| :--- | :--- | :--- |
| **Minecraft** | `1.21.1` | Cliente e Servidor |
| **NeoForge** | `>= 21.1.200` *(testado com 21.1.252)* | Cliente e Servidor |
| **CreativeCore** | `>= 2.13.13` até `< 2.14` | Cliente e **Servidor** |
| **WaterMedia** | `>= 2.1.34` até `< 2.2` | **Apenas Cliente** |

---

## 🛠️ O que foi corrigido nesta versão?

Na versão original `2.1.23` do mod, acessar um servidor multiplayer antes das configurações estarem perfeitamente sincronizadas entre cliente e servidor causava um erro interno (`IllegalStateException`), fechando o jogo do jogador ou impossibilitando o uso.

**A solução (`configfix`):** Implementamos um invólucro de segurança (`safeGet`) em todas as configurações do mod (`DisplaysConfig`). Agora, se o cliente tentar ler uma configuração que ainda não foi carregada pelo servidor, o mod usa o valor padrão de forma segura em vez de "crashar". 

---

## 🌍 Como Instalar Corretamente (Multiplayer)

**Um erro comum é achar que o WaterFrames roda apenas no lado do cliente.** Ele **precisa** estar no servidor! Se você instalar apenas no cliente, sempre que colocar ou olhar para uma TV/Projetor, o seu jogo vai te desconectar com um erro de pacote (ex: *Failed to encode packet 'serverbound/minecraft:custom_payload'* causado por mods como o Jade).

### 🖥️ No Servidor Dedicado
Coloque na pasta `mods` do seu servidor:
1. `waterframes-NEOFORGE-mc1.21.1-v2.1.23-configfix.jar`
2. **CreativeCore** (mesma versão que será usada nos clientes)
> ⚠️ *Nota: O **WaterMedia** não deve ser colocado no servidor.*

### 🎮 No Cliente (Jogadores)
Coloque na pasta `mods` do seu Minecraft:
1. `waterframes-NEOFORGE-mc1.21.1-v2.1.23-configfix.jar`
2. **CreativeCore** (mesma versão do servidor)
3. **WaterMedia** `2.1.34+` (e os plugins opcionais que desejar, como o do YouTube)

---

## ⚙️ Dicas de Configuração e Permissões

* **Mesmos arquivos:** Certifique-se sempre de que o `.jar` do WaterFrames no Servidor é idêntico ao do Cliente. Não misture a versão original com a versão `configfix`.
* **Sistema de Permissões (PermissionAPI):** Nas configurações do servidor (`DisplaysConfig`), **evite ativar** a opção `usePermissionsAPI`. Atualmente, habilitá-la pode derrubar o cliente ao clicar em um display. Deixe desativada para uma experiência sem interrupções.

---

### 📝 Créditos e Licença
* **Mod original e todos os direitos:** [SrRapero720](https://github.com/SrRapero720/waterframes)
* **Modelos:** FabiAcr e J-RAP | **Texturas:** Kotyarendj
* *As modificações desta fork foram feitas com foco em estabilidade para comunidades e submetidas como contribuição (Pull Request) ao autor original.*
