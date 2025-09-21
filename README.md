# Assistente Virtual com PLN (DIO)

Sistema simples de **assistente por voz** com três módulos:
- **TTS (Text-to-Speech)** via `gTTS` (gera MP3 no Colab).
- **STT (Speech-to-Text)** via `SpeechRecognition` + Google Web Speech.
- **Comandos por voz**: busca na **Wikipedia**, pesquisa no **YouTube** e **Google Maps** para “farmácia mais próxima” (ou outros lugares).

> **Stack**: Python 3.x, Google Colab, `gTTS`, `SpeechRecognition`, `pydub`, `wikipedia`.

---

## 🚀 Como executar (Google Colab)

1. Abra o notebook **`AssistenteVirtual_PLN_DIO.ipynb`** no Google Colab.
2. Execute as células **na ordem**:
   - **Passo 1 – TTS**: instala `gTTS` e gera áudios de teste (MP3) com player embutido.
   - **Passo 2 – STT**: instala `SpeechRecognition`/`pydub` e transcreve um áudio curto (upload → conversão para WAV mono 16 kHz → transcrição).
   - **Passo 3 – Comandos por Voz**: interpreta texto/transcrição e executa ações (Wikipedia/YouTube/Maps), com resposta falada curta.

> **Dica**: Após o Passo 2, use a variável `transcript` diretamente no orquestrador do Passo 3:
> ```python
> _ = run_command(transcript)
> ```

---

## 🧠 Comandos suportados (exemplos PT/EN)

- **Wikipedia**
  - `Pesquisar inteligência artificial na Wikipedia`
  - `Search Wikipedia for Alan Turing`
- **YouTube**
  - `Abrir YouTube para lo-fi hip hop`
  - `Open YouTube for python tutorials`
- **Mapas (farmácia mais próxima / lugares)**
  - `Farmácia mais próxima em Orlando`
  - `nearest pharmacy in Boston`
  - `supermercado perto de mim`

O notebook gera:
- **Link clicável** (Wikipedia/YouTube/Maps)
- **Resumo falado** (gTTS) para respostas do Wikipedia ou confirmações (“Abrindo YouTube…”, “Mostrando no mapa…”)

---

## 📁 Estrutura
/ (Colab)
├── tts_outputs/ # MP3 gerados pelo TTS (Passo 1)
├── stt_inputs/ # arquivos enviados para STT (Passo 2)
├── stt_processed/ # WAV 16k mono (Passo 2)
└── assistant_outputs/ # respostas faladas do Passo 3

---

## 🔧 Requisitos

- Google Colab (recomendado).
- Internet ativa (gTTS e STT com backend do Google).
- Áudios curtos (≤ ~60s) funcionam melhor no `recognize_google`; para áudios longos, use chunking (célula opcional).

---

## ⚠️ Limitações & Notas

- `recognize_google` é um serviço online gratuito; pode ter **limites** e **variações de qualidade**.
- `pyttsx3` (TTS offline) foi incluído como **opcional para execução local**; no Colab, tende a não funcionar.
- “Perto de mim” no Maps usa a **localização do navegador** ao abrir o link.

---

## 🧩 Troubleshooting

- **STT não entende**: verifique se o áudio está claro, sem ruído; garanta conversão para **WAV mono 16 kHz**.
- **Erro de API no STT**: tente novamente (instabilidade do backend gratuito).
- **Sem som no player**: verifique o volume e permissões do navegador para mídia.

---

## 📚 Créditos / Referências

- Exemplos de TTS/STT apresentados no curso DIO.
- `gTTS` – https://pypi.org/project/gTTS/
- `SpeechRecognition` – https://pypi.org/project/SpeechRecognition/
- `pydub` – https://pypi.org/project/pydub/
- `wikipedia` – https://pypi.org/project/wikipedia/

---

## 📜 Licença

Este projeto pode ser publicado sob **MIT License** (ajuste conforme necessário).

