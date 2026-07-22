# Corda a Corda 🎸

App/PWA para **aprender violão de ouvido do zero**. Sem dependências externas, sem build, funciona **offline**.

## Recursos
- **Som das notas** com timbre de corda (Web Audio API).
- **Microfone** que escuta e avalia a nota tocada/cantada (detecção de tom por autocorrelação). O acerto é por *classe de nota*, então aceita qualquer oitava — mais tolerante para iniciantes.
- **Repertório** baseado nos guias de melodias: escala de Dó Maior, Cai Cai Balão, Brilha Brilha Estrelinha, Parabéns, Ciranda Cirandinha, Bate o Sino, Atirei o Pau no Gato, Asa Branca, Se Esta Rua Fosse Minha.
- **Dois sistemas de dedilhado**: Multicordas (tradicional) e 1ª Corda (linear), com diagrama do braço.
- **Velocidade** ajustável (40–160 BPM).
- **3 modos por música**: Passo a passo · Tocar melodia · Guiado (microfone).
- **Níveis progressivos** com desbloqueio + progresso salvo no aparelho.
- **Afinador** (agulha de cents + afinação padrão) e **Treino de Ouvido**.

## Rodar localmente
Microfone e service worker exigem **HTTPS ou localhost**. Abrir o `index.html` direto (file://) desliga o microfone.

```bash
# qualquer servidor estático serve; ex.:
python3 -m http.server 8080
# depois acesse http://localhost:8080
```

## Publicar no GitHub Pages
1. Crie um repositório no GitHub (ex.: `corda-a-corda`).
2. Suba os arquivos (veja comandos abaixo).
3. No GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, pasta `/ (root)`. Salve.
4. Em 1–2 min o app fica em `https://SEU_USUARIO.github.io/corda-a-corda/`.

O GitHub Pages já serve por HTTPS, então microfone e instalação como PWA funcionam.

## Estrutura
```
corda-a-corda/
├── index.html        # app inteiro (UI + áudio + microfone + dados)
├── manifest.json     # metadados do PWA
├── sw.js             # service worker (cache offline)
├── .nojekyll         # Pages serve os arquivos sem processar
├── icons/            # ícones (comum + maskable + apple + favicon)
├── LICENSE
└── README.md
```

## Notas técnicas
- Tudo em caminhos **relativos** (`./...`), então funciona em subpasta (`usuario.github.io/repo/`).
- Ao publicar uma nova versão, incremente `VERSION` em `sw.js` para forçar atualização do cache.
