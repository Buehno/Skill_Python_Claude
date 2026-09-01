---
name: python-libraries-toolkit
description: "Cardápio de bibliotecas Python para escolher e usar a biblioteca certa ao desenvolver qualquer projeto (web, desktop, jogos, dados, visão computacional, áudio, NLP, scraping, documentos, bancos de dados, mapas, hardware, bots, matemática). Use ao decidir 'qual biblioteca usar para X', ao iniciar um novo projeto em Python que precisa de uma biblioteca central, ou ao pedir ajuda para programar com qualquer uma das ~80 bibliotecas listadas."
---

<!-- argument-hint: [problema, categoria, ou nome de biblioteca] -->

# Cardápio de Bibliotecas Python
**Fonte**: Cardápio de Bibliotecas — Programação em Python, UniAnchieta, Prof. Dr. Roger Antunes (2026/2) | **Categorias**: 16 | **Bibliotecas**: ~80 | **Gerado**: 2026-09-01

## Como usar esta skill

- **Sem argumento** — carregue os frameworks e o método de escolha abaixo.
- **Com um problema** ("preciso detectar objetos na webcam", "quero gerar um PDF") — encontre a categoria no Índice de Tópicos, leia o capítulo correspondente e recomende/implemente a biblioteca certa.
- **Com uma categoria** (ex: "visão computacional", "web") — carregue o capítulo daquela família.
- **Com o nome de uma biblioteca específica** — consulte glossary.md para a definição rápida e o capítulo para o guia de uso com exemplo de código.
- **"e mais"** — o método (problema → família → biblioteca) e as árvores de decisão em cheatsheet.md funcionam para QUALQUER biblioteca Python, inclusive as que não estão nesta lista. Quando o usuário mencionar uma biblioteca fora do cardápio, aplique o mesmo raciocínio: identifique a família mais próxima, compare trade-offs com as bibliotecas already conhecidas, e ajude a implementar.

Quando a pergunta não estiver coberta no núcleo abaixo, leia o arquivo de capítulo relevante antes de responder.

---

## Método de escolha (regra central da fonte)

Escolha **nesta ordem** — nunca ao contrário:
1. **Problema** — o que o programa precisa fazer de verdade? (contar, decidir, alertar, guardar, mostrar)
2. **Família** — que categoria resolve esse tipo de problema?
3. **Biblioteca** — só então, qual biblioteca específica dentro da família.

Escolher a biblioteca primeiro e procurar um problema depois costuma gerar um projeto artificial e superficial.

## Regras obrigatórias (quando o contexto for um trabalho acadêmico com este cardápio)

- A biblioteca precisa ser **gratuita e instalável via `pip`** — todo o cardápio já atende isso; qualquer biblioteca fora da lista também vale, desde que registrada.
- **IA precisa rodar localmente.** Um projeto cuja "biblioteca de IA" é só um cliente de API na nuvem não atende ao requisito — as bibliotecas de visão/áudio/texto com IA desta lista (YOLO, MediaPipe, face_recognition, DeepFace, EasyOCR, faster-whisper, transformers, sentence-transformers) rodam na máquina, e o projeto é o que se faz com a saída delas.
- A biblioteca escolhida precisa ser o **coração do sistema** — se ela aparece em três linhas do projeto inteiro, o requisito não foi cumprido.
- Antes de fechar a escolha: instale a biblioteca candidata em todas as máquinas do grupo, confirme que dá para demonstrar sem internet (quando aplicável) e que o projeto se divide bem entre os integrantes.

## Frameworks e mental models principais

- **Problema → Família → Biblioteca**: nunca inverta a ordem (ver acima).
- **Manipular vs. entender (visão)**: Pillow/OpenCV manipulam pixels; YOLO/MediaPipe/face_recognition/DeepFace *entendem* o conteúdo. Frequentemente se usa as duas camadas juntas (OpenCV captura → YOLO detecta).
- **Estático vs. dinâmico (web scraping)**: página sem JavaScript → requests+BeautifulSoup; página que só carrega com JS ou exige login → Selenium/Playwright.
- **Ler vs. gerar (documentos)**: pypdf/pdfplumber leem PDF existente; ReportLab/fpdf2 geram PDF do zero — não confundir a direção do problema.
- **Nomes-armadilha**: SymPy (álgebra simbólica) ≠ SimPy (simulação de eventos) — confira o import.
- **A "camada de acabamento" nunca é a biblioteca central**: Rich, Typer, pytest, python-dotenv, cryptography, PyInstaller, tqdm melhoram qualquer projeto mas não substituem a biblioteca-coração da família escolhida.
- **Densidade sobre completude ao recomendar**: prefira uma biblioteca bem aplicada e a fundo a várias usadas superficialmente.

---

## Índice de Capítulos (por categoria)

| # | Categoria | Bibliotecas principais |
|---|-----------|------------------------|
| [ch01](chapters/ch01-web.md) | Web: sites, painéis e APIs | Flask, FastAPI, Streamlit, Gradio, Django, Dash |
| [ch02](chapters/ch02-desktop.md) | Programas de janela (desktop) | Tkinter, CustomTkinter, PySide6, Flet, Kivy, DearPyGui |
| [ch03](chapters/ch03-jogos.md) | Jogos | Pygame, Arcade, Pyglet, Ursina, Pymunk |
| [ch04](chapters/ch04-dados.md) | Dados, planilhas e gráficos | pandas, NumPy, Matplotlib, Seaborn, Plotly, openpyxl, scikit-learn, SciPy |
| [ch05](chapters/ch05-imagem-video.md) | Imagem, foto e vídeo | Pillow, OpenCV, MoviePy, scikit-image, rembg, qrcode/pyzbar |
| [ch06](chapters/ch06-visao-ia.md) | Visão com inteligência artificial | Ultralytics YOLO, MediaPipe, face_recognition, DeepFace, EasyOCR, pytesseract, supervision |
| [ch07](chapters/ch07-audio.md) | Áudio, fala e música | pydub, SpeechRecognition, faster-whisper, pyttsx3, gTTS, librosa, sounddevice |
| [ch08](chapters/ch08-texto-linguagem.md) | Texto e linguagem (NLP) | spaCy, NLTK, rapidfuzz, sentence-transformers, transformers |
| [ch09](chapters/ch09-coleta-web.md) | Coleta de dados na web | requests, BeautifulSoup, Selenium, Playwright, Scrapy, feedparser |
| [ch10](chapters/ch10-documentos.md) | Documentos, PDF e relatórios | python-docx, pypdf, pdfplumber, ReportLab, python-pptx, fpdf2 |
| [ch11](chapters/ch11-armazenamento.md) | Guardar dados | sqlite3, SQLAlchemy, Peewee, TinyDB |
| [ch12](chapters/ch12-mapas.md) | Mapas e localização | folium, geopy, GeoPandas |
| [ch13](chapters/ch13-hardware-automacao.md) | Hardware, sensores e automação | pyserial, gpiozero, paho-mqtt, PyAutoGUI, schedule, watchdog, psutil |
| [ch14](chapters/ch14-bots-integracoes.md) | Bots e integrações | python-telegram-bot, discord.py, smtplib/imaplib |
| [ch15](chapters/ch15-matematica-simulacao.md) | Matemática, simulação e grafos | SymPy, NetworkX, SimPy |
| [ch16](chapters/ch16-acabamento.md) | O acabamento (nunca a biblioteca principal) | Rich, Typer, pytest, python-dotenv, cryptography, PyInstaller, tqdm |

## Índice de Tópicos (problema → categoria)

- **API/backend** → ch01 | **Automação de programas na tela** → ch13
- **Banco de dados** → ch11 | **Bot de chat** → ch14
- **Contagem de objetos/pessoas** → ch06 | **Criptografia/senhas** → ch16
- **Dashboard interativo** → ch01, ch04 | **Detecção de objetos/rosto** → ch06
- **Documentos Word/PDF/PPT** → ch10 | **E-mail automático** → ch14
- **Executável/empacotamento** → ch16 | **Fala para texto / texto para fala** → ch07
- **Gráficos e visualização** → ch04 | **Hardware (Arduino, Raspberry Pi, IoT)** → ch13
- **Interface desktop** → ch02 | **Jogos 2D/3D** → ch03
- **Machine learning clássico** → ch04 | **Mapas e geolocalização** → ch12
- **NLP / entender texto** → ch08 | **OCR (ler texto em imagem)** → ch06
- **Planilhas Excel** → ch04, ch10 | **Processamento de imagem/vídeo** → ch05
- **Raspagem de dados da web (scraping)** → ch09 | **Reconhecimento facial** → ch06
- **Simulação de filas/eventos** → ch15 | **Testes automatizados** → ch16
- **Web scraping dinâmico (JS/login)** → ch09 | **Álgebra/matemática simbólica** → ch15

## Arquivos de apoio

- [glossary.md](glossary.md) — todas as ~80 bibliotecas, alfabético, definição de uma linha + capítulo.
- [patterns.md](patterns.md) — padrões prontos "problema → combinação de bibliotecas", com trade-offs.
- [cheatsheet.md](cheatsheet.md) — árvores de decisão, tabelas de trade-off e sinais de alerta (tells).

---

## Escopo e limites

Esta skill cobre o cardápio de ~80 bibliotecas do documento-fonte (UniAnchieta, Engenharia de Software, 2026/2), organizadas em 16 famílias de problema. As regras "IA local obrigatória" e "biblioteca precisa ser o coração do projeto" vêm do enunciado do trabalho — aplique-as quando o contexto for esse trabalho específico; em projetos gerais elas continuam sendo boas práticas de honestidade técnica, mas não restrições rígidas.

O método (problema → família → biblioteca) e as árvores do cheatsheet.md generalizam para qualquer biblioteca Python além destas 80 — é assim que esta skill cobre "e mais": ao encontrar uma necessidade não listada, identifique a família de problema mais próxima entre as 16 acima, e recomende/implemente por analogia com as bibliotecas já documentadas.
