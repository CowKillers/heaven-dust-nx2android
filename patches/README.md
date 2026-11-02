# Patches deste port

Dois patches, nenhum arquivo do jogo, nenhuma chave, nenhum shader
traduzido e nenhum módulo patchado.

## unityfs-shader-2019-2.patch

Adiciona ao `nxnative/dm/gfx/tools/unityfs.py` o layout `SHADER_2019_2`
e a entrada correspondente em `KNOWN_TREES` para o hash
`ba38e7fa8c2561e09fad219bd4b98f3b` (Unity 2019.2.15f1, o do Heaven Dust).

Sem ele, o port trava no passo 4/8 (shader split), porque o jogo tem
arquivos Unity sem type trees e nenhum layout conhecido lê o Shader dele.

**Base e teste:** aplica limpo no `unityfs.py` do nx2android upstream
`ba7499a` (verificado com `git apply --check` e import do módulo: o
`SHADER_2019_2` entra em `KNOWN_TREES` e nenhum outro layout novo vem
junto — o `SHADER_5_5` do Ben 10, que vive no mesmo arquivo no clone
local, **não** está neste patch).

```sh
# a partir da raiz do clone do nx2android, em ba7499a:
git apply /caminho/para/heaven-dust-nx2android/patches/unityfs-shader-2019-2.patch
```

## host-screen-modes.patch

Muda o host Android (`nxnative/dm/android/front_android.c`,
`gfx_vk_present.c`, `overlay_layout.h`) para os 3 modos de tela do
launcher v6:

- **Fit** (padrão): proporção mantida, faixas pretas.
- **Stretch**: tela cheia, imagem distorcida.
- **Crop**: tela cheia sem distorção, cortando o meio da fonte em
  cima/embaixo, com o toque mapeado para o sub-retângulo visível
  (`g_pic` passa de `uint32_t` para `int32_t` para o retângulo
  negativo do Crop).

O modo vive em `settings.txt` como `screen=0/1/2`, nos bits 28–29 do
estado do menu, e aparece como linha `Screen` na aba Game do menu
interno. O patch inclui também o tema do menu interno do launcher
(painel #0E151A, acento #B08D57), que é o tema da v2 em diante.

**Base e teste — leia antes de aplicar:** este patch foi gerado como o
diff entre o estado do clone usado na build v6 e a cópia `dm-copy`
usada para buildar o host da v6, e foi verificado aplicando limpo
nesse estado. Ele **não** aplica limpo no upstream `ba7499a` puro,
porque o clone já carrega outras mudanças locais nesses mesmos
arquivos (entre elas o Hide do Alex Kidd). Para reproduzir o host da
v6, aplique primeiro as mudanças locais do clone e depois este patch,
ou use o diff como referência das linhas exatas do Heaven Dust.

```sh
# no estado do clone usado na build v6:
git apply /caminho/para/heaven-dust-nx2android/patches/host-screen-modes.patch
```
