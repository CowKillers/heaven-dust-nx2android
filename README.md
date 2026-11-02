# Heaven Dust no Android (nx2android)

Port experimental de **Heaven Dust** (Switch) para Android, feito com o
[nx2android](https://github.com/shirai91/nx2android) — o código arm64 do jogo roda
nativamente no celular, com o host substituindo os serviços do Switch e o NVN
reproduzido em Vulkan, sem emulador.

> **Experimental — sem release.** Este repositório não contém o jogo, as chaves,
> o APK, os dados, os shaders nem nenhum arquivo extraído do jogo. Não há release
> aqui, e não haverá, até que o port esteja provado no aparelho.

## Estado atual (02/11/2026, honesto)

- Port experimental construído com o porter do nx2android
  (`porter port --experimental --debug`): perfil provisório adivinhado pelo survey,
  porque o jogo **não tem perfil** no nx2android para o title
  `010059100D928000`.
- O jogo é Unity **2019.2.15f1**, IL2CPP, NVN, FMOD, Nintendo SDK **9_3_1**
  (o host é convertido para SDK 16 — esse descompasso é um risco ainda não
  provado, só o log do aparelho responde).
- O split de shaders traduziu **2.924 de 2.924 shaders** para Vulkan
  (pacote de 44 MB), sem falha. O primeiro port travou no passo 4/8 porque
  o hash de Shader do Unity 2019.2 não estava nos layouts conhecidos do
  `unityfs.py`; o layout `SHADER_2019_2` foi derivado do próprio jogo e o
  segundo port completou 8/8.
- APK gerado pelo porter: pacote `org.nx2a.t010059100d928000`,
  versionCode 1, versão do jogo 1.0.2, build debug (gera `log.txt`).
- Data pack gerado pelo porter: 47 arquivos, 0,7 GB
  (`RomFS/`, `mods/`, `shaders.dmsv`, `env.txt`, `nintendo_ext.ttf`,
  `nx2a-data.json`).
- Launcher à parte (não está neste repositório): importação do data pack
  por SAF, Configuração (docked, FPS, gamepad, opacidade, vibração),
  drivers de GPU com Turnip, e 3 modos de tela — Fit, Stretch e Crop —
  na Configuração do launcher e no menu interno do jogo.
- **O que já se sabe no aparelho:** o launcher abre no Galaxy S23 e a
  tradução PT-BR 1.1 abaixo foi aplicada e confirmada funcionando no
  aparelho em 01/11/2026. Não trate este port como jogável até o fim:
  nada além disso foi provado até aqui.

## Tradução PT-BR

Existe uma tradução PT-BR para Switch do Heaven Dust 1 (porte da tradução
de PC, Central de Traduções), em formato LayeredFS
(`010059100D928000/romfs/Data/`). A pasta certa para este jogo é a
**Versão 1.1** — não a 1.0, que é de uma build mais antiga.

No port Android, a tradução **não** vai por Atmosphere e **não** vai na
pasta `mods/` (que é só para módulos de código). Ela se aplica
substituindo, com backup dos originais, estes 2 arquivos em
`Android/data/org.nx2a.t010059100d928000/files/RomFS/Data/`:

- `globalgamemanagers.assets`
- `resources.assets`

## Mini tutorial — como instalar

### Requisitos

- Android arm64, com Vulkan. Alvo do teste: Galaxy S23 (Adreno 740, Vulkan 1.3).
- O APK sozinho **não** é o jogo: ele é só o executável do port.

### Passo 1 — Gere os seus próprios dados

**Os dados NÃO vêm no APK e NÃO estão neste repositório.** Você precisa gerar
o seu próprio pacote de dados com o porter do nx2android, a partir do
**seu próprio dump do jogo (NSP) e das suas próprias chaves** — nunca baixe
nem compartilhe RomFS, NSP, shaders ou chaves de terceiros.

O port experimental usa:

```sh
python -m porter port <pasta-do-jogo> --experimental --debug
```

### Passo 2 — Coloque os dados do jogo no lugar certo

Depois de gerar o pacote, copie o conteúdo **solto** (sem pasta extra no meio)
para:

```
Android/data/org.nx2a.t010059100d928000/files/
```

A pasta tem que ficar assim:

```
Android/data/org.nx2a.t010059100d928000/files/
├── RomFS/
├── mods/
├── shaders.dmsv
├── env.txt
└── nx2a-data.json
```

O `shaders.dmsv` vai **na raiz de `files/`**, não dentro de `mods/` e não com
outro nome. Se você desinstalar o app, **o Android apaga essa pasta inteira**
(dados e saves). Depois de reinstalar, copie os dados de novo.

### Passo 3 — Instale o APK gerado pelo porter e abra o jogo

1. Instale o APK gerado na pasta do jogo.
2. Abra o jogo. Se ele parar sem os dados, é porque a pasta acima ainda não
   está completa — complete os dados antes de concluir qualquer coisa sobre o port.

### Log

O build debug escreve o log em:

```
Android/data/org.nx2a.t010059100d928000/files/log.txt
```

A cada novo lançamento, o log anterior vira `log.prev.txt`. Copie o `log.txt`
**antes** de abrir o jogo de novo, senão a sessão do problema se perde.

## Canais do CowKillers

🎬 Canal no YouTube: https://youtube.com/@emuucheck

💬 Grupo no Telegram — testes e apoio: https://t.me/+nPJwnuKuAh5iNzhh

Quem quiser testar e apoiar o projeto, entra por lá. Novidades e próximos
passos são publicados primeiro no grupo.

## O que este repositório NÃO contém

- Nenhum arquivo do jogo (NSP, XCI, RomFS, shaders, dados extraídos,
  data pack ou zip de data pack).
- Nenhum módulo patchado (`mods/*.patched.bin`).
- Nenhuma chave (`prod.keys`, chave de assinatura ou qualquer arquivo
  de chave).
- Nenhum log, save ou `env.txt` de aparelho.
- O APK **não** está neste repositório e não há release aqui.

Cada pessoa precisa do próprio dump do jogo e das próprias chaves. Não
distribua arquivos do jogo nem chaves.

## Créditos

- [nx2android](https://github.com/shirai91/nx2android) (shirai91) — a base
  de recompilação usada pelo port.
- Heaven Dust © seus respectivos donos.
