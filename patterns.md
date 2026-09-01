---
name: patterns
description: Padrões "problema → biblioteca(s)" para desenvolver um projeto Python do zero usando o cardápio de bibliotecas.
---

# Padrões de solução (problema → biblioteca)

## Método de escolha (o princípio central do documento-fonte)
Escolha nesta ordem, nunca ao contrário:
1. **Problema** — o que precisa ser resolvido de verdade (contar, decidir, alertar, guardar, mostrar)?
2. **Família** — qual categoria resolve esse tipo de problema (web, desktop, visão, dados...)?
3. **Biblioteca** — só então, qual biblioteca específica dentro da família.

Escolher a biblioteca primeiro ("quero usar YOLO") e procurar um problema depois costuma gerar projetos artificiais. Comece pelo problema real.

## Padrões comuns

### "Quero contar/detectar algo em imagem ou vídeo e reagir a isso"
**Como**: OpenCV (ch05) ou webcam → Ultralytics YOLO / MediaPipe (ch06) para detectar → supervision (ch06) para contar cruzamentos/zonas → pandas (ch04) para registrar → alerta via python-telegram-bot (ch14) ou exibição em Streamlit (ch01).
**Trade-off**: YOLO é mais pesado (precisa baixar modelo, GPU ajuda mas não é obrigatória); MediaPipe é mais leve e roda bem em qualquer notebook.

### "Quero um painel para o usuário ver dados/gráficos"
**Como**: pandas (ch04) processa os dados → Streamlit ou Dash (ch01) exibe → Plotly/Seaborn (ch04) para os gráficos.
**Trade-off**: Streamlit é mais rápido de montar; Dash dá mais controle fino de interatividade (callbacks).

### "Quero automatizar leitura de documentos (PDF/planilha) e gerar um relatório"
**Como**: pdfplumber ou pypdf (ch10) lê o PDF de entrada → pandas (ch04) processa → python-docx ou ReportLab/fpdf2 (ch10) gera a saída → openpyxl (ch04) se a saída for planilha.
**Trade-off**: se o PDF de entrada for escaneado (imagem), precisa de OCR (EasyOCR/pytesseract, ch06) antes de qualquer extração de texto.

### "Quero um bot que avisa as pessoas sobre algo"
**Como**: watchdog (ch13) ou schedule (ch13) detecta o evento/horário → lógica de decisão em Python → python-telegram-bot ou discord.py (ch14) envia o alerta. python-dotenv (ch16) protege o token do bot.
**Trade-off**: Telegram é mais simples para alertas 1:1; Discord é melhor para comunidades/grupos.

### "Quero coletar dados da internet e analisar"
**Como**: requests + BeautifulSoup (ch09) para páginas estáticas, ou Playwright/Selenium (ch09) se a página precisa de JavaScript/login → pandas (ch04) organiza → Matplotlib/Plotly (ch04) mostra.
**Trade-off**: Scrapy compensa a partir de dezenas/centenas de páginas do mesmo site; para poucas páginas, requests+BeautifulSoup é mais simples.

### "Quero transcrever áudio/vídeo e processar o texto"
**Como**: faster-whisper (ch07) transcreve localmente (sem internet) → spaCy/NLTK (ch08) extrai informação do texto → pandas (ch04) organiza os resultados.

### "Quero um jogo ou simulação visual"
**Como**: Pygame/Arcade (ch03) para 2D → Pymunk (ch03) se precisar de física real → Pillow (ch05) prepara os sprites.

### "Quero um app desktop que também funcione perto de hardware físico"
**Como**: pyserial (ch13) lê o Arduino/sensor → DearPyGui (ch02) mostra os dados ao vivo (atualização rápida) → sqlite3 (ch11) guarda o histórico.

### "Quero identificar/reconhecer pessoas ou objetos específicos"
**Como**: face_recognition (ch06) para "quem é" contra um cadastro; DeepFace para idade/emoção/verificação; Ultralytics YOLO para "o quê e onde" (objetos genéricos, não identidade).
**Cuidado**: reconhecimento facial levanta questões de privacidade — use com consentimento, especialmente em projeto acadêmico.

### "Quero mapear algo geograficamente"
**Como**: geopy (ch12) converte endereços em coordenadas → folium (ch12) desenha o mapa interativo → GeoPandas (ch12) se precisar cruzar com regiões/bairros para análise agregada.

## Padrão de "acabamento" (aplica-se a qualquer projeto)
Todo projeto, independente da família escolhida, deve considerar: Rich/tqdm (feedback visual no terminal), pytest (provar que funciona), python-dotenv (proteger credenciais), PyInstaller (se for entregar um executável). Nenhuma dessas é a biblioteca "coração" do projeto — ver Regra de Ouro no SKILL.md.
