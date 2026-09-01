---
name: cheatsheet
description: Referência rápida de decisão — árvores e tabelas para escolher biblioteca Python sem reler os capítulos.
---

# Cheatsheet de Decisão

## Regra de ouro (aplica-se a qualquer escolha)
1. Problema primeiro, família depois, biblioteca por último.
2. A biblioteca de IA precisa rodar **localmente** — um mero cliente de API de nuvem não conta.
3. A biblioteca escolhida precisa ser o **coração** do projeto: se ela aparece em 3 linhas do código inteiro, o requisito não foi cumprido.
4. Teste a instalação em TODAS as máquinas do grupo antes de fechar a escolha.
5. Confirme se dá para demonstrar **sem internet** (elimina gTTS/SpeechRecognition/geocoding pesado se a demo for offline).
6. Confirme se o projeto se divide bem entre os integrantes do grupo.
7. Gratuita + `pip install` é pré-requisito — todo o cardápio já atende isso.

## Árvore: "que tipo de interface eu preciso?"
- Roda no navegador?
  - Só eu/grupo vê, é análise de dados → **Streamlit**
  - Demo de uma função de IA (upload/webcam) → **Gradio**
  - Público geral, com login/permissões/admin → **Django**
  - API pura para outro sistema consumir → **FastAPI**
  - Dashboard com muitos filtros interativos → **Dash**
  - Quero controle total do HTML → **Flask**
- Roda como janela no computador?
  - Simples, sem instalar nada extra → **Tkinter** (ou **CustomTkinter** para ficar bonito)
  - Precisa parecer software comercial → **PySide6**
  - Precisa também rodar em celular/web com o mesmo código → **Flet**
  - Precisa atualizar tela dezenas de vezes por segundo (sensor ao vivo) → **DearPyGui**
- Roda em celular com toque?
  - **Kivy**
- É um bot dentro de um app de chat?
  - Telegram → **python-telegram-bot** · Discord → **discord.py**

## Árvore: "preciso processar imagem/vídeo — qual ferramenta?"
- Só editar (cortar/redimensionar/filtro) → **Pillow**
- Processar vídeo/webcam quadro a quadro → **OpenCV**
- Detectar/contar objetos ou pessoas → **Ultralytics YOLO** (+ **supervision** para contagem/zonas)
- Rastrear mão/rosto/corpo em tempo real → **MediaPipe**
- Saber QUEM é a pessoa (contra cadastro) → **face_recognition**
- Estimar idade/emoção → **DeepFace**
- Ler texto na imagem → **EasyOCR** (multilíngue) ou **pytesseract** (documento escaneado limpo)
- Editar arquivo de vídeo (cortar, sobrepor texto) → **MoviePy**
- Remover fundo → **rembg**

## Trade-offs: velocidade vs. robustez (coleta web)
| Cenário | Ferramenta | Por quê |
|---|---|---|
| Página estática, poucas páginas | requests + BeautifulSoup | Mais leve e rápido |
| Página com JavaScript/login | Selenium ou Playwright | Só eles executam JS e simulam clique |
| Muitas páginas do mesmo site | Scrapy | Paralelismo e exportação prontos |
| Feed de notícias já estruturado | feedparser | Não precisa nem de parsing de HTML |

## Trade-offs: banco de dados
| Escala do projeto | Use |
|---|---|
| Uma tabela, sem servidor | sqlite3 puro |
| Várias tabelas, pode trocar de banco no futuro | SQLAlchemy |
| ORM simples, aprendido rápido | Peewee |
| Dados sem esquema fixo, tipo dicionário | TinyDB |

## Tells (sinais de que algo está errado)
- Nomes parecidos, cuidado ao importar: **SymPy** (álgebra) ≠ **SimPy** (simulação).
- Se você está reimplementando física de colisão manualmente em um jogo → falta **Pymunk**.
- Se você está comparando strings com `==` para achar duplicatas de nome → falta **rapidfuzz**.
- Se o projeto chama uma API de nuvem de IA e só mostra o resultado cru → não atende ao requisito do trabalho (precisa processar localmente e agir sobre a saída).
- Se uma biblioteca do grupo "Acabamento" (ch16) é a única lógica do projeto → biblioteca central errada, escolha uma de verdade.
- Token/senha aparecendo direto no código → falta **python-dotenv**.

## Limiares e padrões úteis
- YOLO: comece pelo modelo **nano** (`yolov8n.pt`); só suba de tamanho se a precisão não bastar.
- Scraping: sempre intercale `time.sleep()` entre requisições em massa para não sobrecarregar o site.
- OCR: **EasyOCR** para português/multilíngue geral; **pytesseract** quando o documento é escaneado, limpo e a velocidade importa.
- Fala↔texto offline: **faster-whisper** (fala→texto) e **pyttsx3** (texto→fala) — nenhuma depende de internet.
