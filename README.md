# ConversorLivre
Esse programa grátis converte vídeo, PDF, Word e Excel sem instalar nada (e sem anúncios)
[README.md](https://github.com/user-attachments/files/35437966/README.md)
<div align="center">

<img src="assets/icone.png" width="96" alt="Ícone do Conversor Livre">

# Conversor Livre

**Conversor de arquivos gratuito, de código aberto e sem anúncios para Windows.**
Vídeo, áudio, imagem, PDF, Word e Excel em uma interface simples e moderna, funcionando 100% offline.

![Versão](https://img.shields.io/badge/versão-1.9.0-7c5cff)
![Windows](https://img.shields.io/badge/Windows-10%20%7C%2011%20%7C%20Server%202016%2B-0078D6)
![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB)
![Licença](https://img.shields.io/badge/licença-MIT-green)

</div>

![Tela de conversão de vídeo](docs/tela_video.png)

---

## Sumário

- [Recursos](#recursos)
- [Download e instalação](#download-e-instalação)
- [Como usar](#como-usar)
- [Buscar em pasta](#buscar-em-pasta)
- [Enviar originais para a Lixeira](#enviar-originais-para-a-lixeira)
- [Reduzir PDF de scanner](#reduzir-pdf-de-scanner)
- [Legenda automática e OCR](#legenda-automática-e-ocr)
- [Se aparecer um erro](#se-aparecer-um-erro)
- [Rodar a partir do código-fonte](#rodar-a-partir-do-código-fonte)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Licenças](#licenças)

---

## Recursos

| Aba | O que faz |
|-----|-----------|
| **Vídeo** | Converte para MP4, MKV, WEBM, AVI, MOV e GIF. Escolha de qualidade e resolução (4K a 360p), **cortar trecho** com prévia, **remover o áudio** e **legenda automática** (gera legenda a partir da fala). |
| **Áudio** | MP3, M4A (AAC), WAV, FLAC, OGG e OPUS. Também extrai o áudio de vídeos. |
| **Imagem** | JPG, PNG, WEBP, BMP, ICO e TIFF, com redução de tamanho (ex.: máximo 1920 px). |
| **Documentos** | PDF → Word, **OCR → Word** (foto ou PDF digitalizado vira texto editável), PDF → PNG/JPG, imagens → PDF e juntar PDFs. |
| **Word, Excel e PDF** | Cria uma cópia leve de `.docx`, `.xlsx`, `.pptx` e `.pdf` para enviar por e-mail: reduz as fotos, **remove as partes cortadas** das imagens e **reduz PDFs de scanner** sem perder a leitura. |

E em todas as abas:

- Arrastar e soltar arquivos ou pastas inteiras, com fila e progresso por arquivo.
- **Buscar em pasta**: encontra os arquivos de uma pasta e de todas as subpastas e mostra uma árvore para escolher (vídeo, imagem e Word/Excel/PDF).
- **Enviar originais para a Lixeira** depois de converter (vídeo, imagem e Word/Excel/PDF), sempre recuperável.
- Nunca sobrescreve: se já existe um arquivo com o mesmo nome, cria `nome (1).ext`.
- Aviso antes de fechar se ainda houver uma conversão em andamento.
- Registro de erros (`logs/conversor.log`) e botão **Ver detalhes** em cada arquivo com erro.

## Download e instalação

A forma mais fácil é a **versão portátil**, que já traz o Python e todos os componentes. Não precisa instalar nada.

1. Baixe o arquivo `ConversorLivre_Portatil.zip` na página de [**Releases**](../../releases).
2. Extraia a pasta onde quiser: `C:\`, pendrive, servidor ou pasta de rede.
3. Abra o **`ConversorLivre.exe`**.
   Se o antivírus bloquear o `.exe` (ele não tem assinatura digital), use o **`Iniciar (alternativo).bat`**.

**Requisitos:** Windows 10, Windows 11 ou Windows Server 2016/2019/2022/2025, sempre 64 bits.

> A versão portátil usa Python 3.10 e Qt 5.15 justamente para funcionar também no Windows Server 2016.
> Não apague nem renomeie as pastas `app` e `python` que ficam ao lado do `.exe`.

## Como usar

1. Escolha a aba na barra lateral (Vídeo, Áudio, Imagem, Documentos ou Word, Excel e PDF).
2. Clique no **formato de saída** desejado.
3. Adicione arquivos: arraste para a janela, clique em **Adicionar** ou use **Buscar em pasta**.
4. Ajuste as opções, se quiser:
   - **Qualidade** e **Resolução/Tamanho**;
   - **Mesma pasta** (cada resultado fica ao lado do original) ou **Escolher…** uma pasta de saída.
5. Clique em **Converter**.
6. Ao terminar, clique em **Mostrar** na linha do arquivo para abrir a pasta do resultado.

### Cortar um vídeo

Na aba **Vídeo**, clique em **Cortar** na linha do arquivo. Arraste as duas alças para marcar o início e o fim, ou digite o tempo exato. A prévia mostra a imagem do ponto escolhido. Cada vídeo da fila pode ter um corte diferente.

![Janela de corte](docs/janela_corte.png)

## Buscar em pasta

Ideal para pastas com muitos arquivos espalhados em subpastas (ex.: a pasta da Qualidade).

1. Clique em **Buscar em pasta**, ao lado de "Adicionar".
2. Escolha a pasta. O programa procura nela e em todas as subpastas.
3. Uma **árvore** mostra cada pasta com a quantidade e o tamanho dos arquivos. Tudo vem marcado: desmarque o que não quiser.
4. Clique em **Adicionar à fila** e depois em **Converter**.

Ao usar a busca, a opção **Mesma pasta** é ligada sozinha: cada arquivo convertido fica ao lado do seu original.

![Buscar em pasta](docs/buscar_em_pasta.png)

A busca **pula automaticamente**, e isso pode ser mudado nas opções da janela:

- arquivos já convertidos (o resultado já existe ao lado do original), para poder rodar de novo na mesma pasta sem repetir trabalho;
- cópias criadas pelo programa (`_reduzido`, `_convertido`).

A busca **nunca entra** em: Lixeira, pastas do Windows e de programas, pastas ocultas, arquivos temporários do Office (`~$`) e arquivos vazios.

## Enviar originais para a Lixeira

Nas abas **Vídeo**, **Imagem** e **Word, Excel e PDF** há o botão **Enviar originais para a Lixeira**, ao lado de "Abrir pasta de saída". Quando ligado, ele fica laranja.

- **Ligado:** quando um arquivo termina de converter **sem erro**, o original vai para a **Lixeira do Windows**, como a tecla Delete. Dá para restaurar.
- **Desligado:** o original nunca é tocado.
- Se a conversão der erro, o original fica onde está.
- Ao reduzir no mesmo formato (ex.: JPG → JPG menor, ou Word/Excel/PDF reduzido), o arquivo novo **assume o nome do original**.
- Em **pasta de rede, unidade mapeada ou pendrive** o original é **mantido**: nesses lugares não existe Lixeira e o Windows apagaria o arquivo de vez.

## Reduzir PDF de scanner

PDFs criados por scanners e impressoras costumam ser enormes: cada página é uma foto em alta resolução, quase sempre colorida, mesmo quando o papel é preto e branco. Na aba **Word, Excel e PDF**, o programa:

1. reduz a resolução das páginas só até o necessário para ficar nítido: **Para e-mail** 150 ppi, **Para tela** 200 ppi, **Para impressão** 300 ppi;
2. recomprime as páginas em JPEG de boa qualidade;
3. guarda em tons de cinza apenas as páginas **sem nenhuma cor**: assinatura azul, carimbo e fotos coloridas continuam coloridos;
4. limpa objetos repetidos dentro do PDF.

![PDF antes e depois](docs/pdf_antes_depois.png)

*Exemplo: digitalização colorida de 300 ppi com 6,5 MB → 0,26 MB (e-mail) e 0,56 MB (tela).*

O texto (inclusive o texto pesquisável que alguns scanners adicionam), os links e os marcadores ficam iguais. **Não são alterados:** PDFs com senha, PDFs **assinados digitalmente** (a assinatura deixaria de valer) e digitalizações em preto e branco puro de 1 bit (que já são pequenas).

### Word, Excel e PowerPoint

O Office guarda a foto inteira mesmo quando você **corta** uma imagem; ele só esconde a parte cortada. O programa apaga essa parte de verdade, reduz a resolução de acordo com o tamanho em que a foto aparece na página e recomprime. Texto, tabelas, fórmulas e formatação ficam iguais.

![Aba Word, Excel e PDF](docs/tela_word_excel_pdf.png)

## Legenda automática e OCR

**Legenda automática (aba Vídeo):** reconhece a fala do vídeo e gera a legenda no próprio computador, sem enviar nada para a internet. Ela pode sair de três formas:

- **arquivo `.srt`** ao lado do vídeo;
- **faixa no vídeo**, que pode ser ligada e desligada no player (MP4, MKV, MOV e WEBM);
- **gravada na imagem**, aparecendo em qualquer player.

Na primeira vez, o programa baixa o modelo de reconhecimento de fala do site huggingface.co e guarda em `app\modelos`. Tamanhos: Rápida ~145 MB, Equilibrada ~480 MB, Máxima ~1,5 GB. Depois disso funciona sem internet. Se a rede bloquear o download, baixe os arquivos `config.json`, `model.bin`, `tokenizer.json` e `vocabulary.txt` de `huggingface.co/Systran/faster-whisper-small` e coloque em `app\modelos\small\`.

**OCR (aba Documentos):** transforma foto ou PDF digitalizado em texto editável no Word. Usa o reconhecimento de texto que **já vem no Windows 10/11**, sem nada para baixar. Opcionalmente, usa o Tesseract, se estiver instalado. Se aparecer um aviso de idioma, adicione o idioma em *Configurações > Hora e idioma > Idioma*, com o recurso de reconhecimento ótico.

## Se aparecer um erro

- Na linha do arquivo com erro, clique em **Ver detalhes** para ler o motivo completo.
- Tudo o que o programa faz fica registrado em **`app\logs\conversor.log`**. Para abrir a pasta, clique em **Abrir registro (log)**, no canto inferior esquerdo da janela.
- Se a pasta do programa não permitir gravação, o log vai para `%LOCALAPPDATA%\ConversorLivre\logs`.
- Ao abrir um *issue* aqui no GitHub, anexe o `conversor.log`.

## Rodar a partir do código-fonte

Requer Python 3.10 ou mais novo (marque *"Add python.exe to PATH"* na instalação).

```bat
git clone https://github.com/SEU-USUARIO/ConversorLivre.git
cd ConversorLivre
executar.bat
```

Na primeira vez, o `executar.bat` cria um ambiente virtual (`.venv`) e instala as dependências do `requirements.txt`. Para rodar manualmente:

```bat
python -m venv .venv
.venv\Scripts\pip install -r requirements.txt
.venv\Scripts\python main.py
```

O programa funciona tanto com **PySide6 (Qt 6)** quanto com **PySide2 (Qt 5.15)**. A camada `qtbind/` escolhe automaticamente a que estiver disponível. Use o Qt 5 para máquinas com Windows 10 antigo ou Windows Server 2016.

Para gerar um executável com PyInstaller, use o **`gerar_exe.bat`**. O resultado sai em `dist\ConversorLivre\`.

> **Dica para o repositório:** não faça commit do `ConversorLivre_Portatil.zip`, porque ele passa de 250 MB. Anexe o zip a uma *Release* do GitHub, que aceita arquivos de até 2 GB.

## Estrutura do projeto

```
main.py           ponto de entrada (trata erros de inicialização)
ui.py             janela principal: abas, cartões de formato, fila e conversão em segundo plano
engine.py         motor de conversão (FFmpeg, Pillow, PDF) e busca em pastas
office.py         redução e recorte real das fotos em Word/Excel/PowerPoint
pdfreduce.py      redução de PDFs (scanner/impressora)
subtitles.py      legenda automática (faster-whisper) e escrita do .srt
ocr.py            reconhecimento de texto (OCR do Windows ou Tesseract)
trim_dialog.py    janela de corte de vídeo com prévia
folder_scan.py    janela "Buscar em pasta" com árvore
trash.py          envio seguro para a Lixeira do Windows
applog.py         registro de eventos e erros
theme.py          cores e estilo (troque a cor de destaque em C["accent"])
icons.py          ícones vetoriais (SVG)
qtbind/           compatibilidade PySide6 / PySide2
assets/           ícone do programa
docs/             imagens deste README
executar.bat      roda a partir do código-fonte
gerar_exe.bat     gera o executável com PyInstaller
```

**Para adicionar um formato:** inclua um `OutputFormat` na lista da categoria em `engine.py` e trate a chave em `ffmpeg_args()` (vídeo e áudio) ou em `convert_image()` (imagem). A interface cria o cartão sozinha.

## Licenças

O código do Conversor Livre está sob a licença **MIT** (veja [`LICENSE`](LICENSE)).

O programa usa bibliotecas de terceiros, cada uma com a sua licença:

| Componente | Uso | Licença |
|------------|-----|---------|
| [FFmpeg](https://ffmpeg.org) (via imageio-ffmpeg) | vídeo e áudio | GPL |
| [PySide6 / PySide2 (Qt)](https://www.qt.io/qt-for-python) | interface | LGPL v3 |
| [Pillow](https://python-pillow.org) | imagens | HPND |
| [pypdf](https://github.com/py-pdf/pypdf) / [pypdfium2](https://github.com/pypdfium2-team/pypdfium2) | PDF | BSD / Apache 2.0 |
| [PyMuPDF](https://pymupdf.readthedocs.io) | redução de PDF e PDF → Word | AGPL v3 |
| [pdf2docx](https://github.com/ArtifexSoftware/pdf2docx) | PDF → Word | MIT |
| [faster-whisper](https://github.com/SYSTRAN/faster-whisper) | legenda automática | MIT |
| [lxml](https://lxml.de) | arquivos do Office | BSD |
| [pywinrt](https://github.com/pywinrt/pywinrt) | OCR do Windows | MIT |

> **Atenção ao distribuir o pacote pronto (zip/exe):** como ele inclui o FFmpeg (GPL) e o PyMuPDF (AGPL),
> quem distribui precisa disponibilizar o código-fonte junto, e este repositório público já cumpre esse papel.
> Inclua também os avisos de licença dessas bibliotecas.
