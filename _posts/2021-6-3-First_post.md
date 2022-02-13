---
layout: post
title: WUFIplus batch mode
category: OT
tags: WUFI, HMT, BES
author: Michele Libralato
---
EN:

For some reason WUFIplus manual instructions to activete batch mode don't work on every system. With this workaround it worked:

1. Add WUFIplus.exe path to environment variables
  - Open Start search and type `variables`, click on `Edit the system environment variables`
  - Click on `Environment Variables...`
  - Under `System variables` in the lower half of the window, look for the `Path` row, click on it, then click on edit
  - Two options: Click `New` and add the `WUFIPlus.exe` path, it usually is `C:\Program Files (x86)\WUFI\masterWUFI\WUFIplus`. If "New" is not available, add the path in the list of paths, in the `variable value` section, after a `;`
  - Click `OK`
2. Open the project folder in a cmd prompt
  - Open Start search and type `cmd.exe` and click on `Command Prompt`
  - copy the path of the folder containing the WUFIplus project files (`.mwp` files)
  - type in the command line `cd`, press space, then paste the path of the project files
3. Enter `wufiplus "C" "R" "filename1.mwp" "filename2.mwp"` where filename1.mwp and filename2.mwp are the previously prepared project files. More files could be added after these two.
  - `"C"` means that WUFIplus will run all the cases in the project files listed
  - `"R"` means that WUFIplus will export the results in two `.txt` files, one containing a report, the second containing the hourly results of the simulation
If you input "R" first and then "C" wufi will not run the simulation.

Is it working?

IT:

Per qualche motivo, usando alla lettera le istruzioni fornite dal manuale di WUFIplus, la modalità batch non funziona. Con questo workaround invece funziona:
1. Aggiungere il percorso dell'eseguibile WUFIplus.exe alle variabli d'ambiente
  - Cliccare su Start e scrivere `variabili` o `ambiente` , cliccare `modifica le variabili d'ambiente relative al sistema`
  - Click su `Variabili d'ambiente...`
  - Nella sezione `Variabili di sistema` nella metà inferiore della finestra, cliccare sulla riga `Path`, e poi su `Modifica...`
  - Ora ci sono due opzioni: Click su `Nuovo` e aggiungere il percorso di `WUFIPlus.exe`, che di solito è `C:\Program Files (x86)\WUFI\masterWUFI\WUFIplus`, oppure, nel caso compaia solo una finestrella con due campi, inserire il percorso nel secondo campo `valore variabile`, dopo un punto e virgola `;`
  - `OK`
2. aprire la cartella dei file di progetto nella riga di comando
  - Click su Start, scrivere `cmd.exe` e click su `Prompt dei comandi`
  - copiare il percorso della cartella che contiene i WUFIplus project files (con estensione`.mwp`)
  - scrivere nella riga di comand `cd` lasciare uno spazio e incollare il percorso della cartella
3. Scrivere `wufiplus "C" "R" "filename1.mwp" "filename2.mwp"` dove filename1.mwp and filename2.mwp sono dei file progetto preparati precedentemente. Si possono aggiungere altri file inserendo il loro nome, uno dopo l'altro .
  - `"C"` significa che WUFIplus simulerà tutti i casi del progetto
  - `"R"` significa che WUFIplus esporterà i risultati in due file `.txt`,uno con un report generale , l'altro con i risultati orari della simulazione
Se scrivi "R" e poi "C" wufi non funzionerà.

Fammi sapere se funziona!
