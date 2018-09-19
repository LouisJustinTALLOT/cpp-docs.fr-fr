---
title: E/S de flux | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ab13141c573ad302528a09b74cb3a5e2aaa0382
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035216"
---
# <a name="stream-io"></a>E/S de flux

Ces fonctions permettent de traiter des données de tailles et de formats différents, des caractères uniques jusqu'aux structures de données volumineuses. Elles assurent aussi une mise en mémoire tampon, ce qui peut améliorer les performances. La taille par défaut d'une mémoire tampon de flux est de 4 Ko. Ces routines concernent uniquement les mémoires tampons créées par les routines de bibliothèque Runtime et n'ont aucun effet sur les mémoires tampons créées par le système d'exploitation.

## <a name="stream-io-routines"></a>Routines d'E/S de flux

|Routine|Utilisez|
|-------------|---------|
|[clearerr](../c-runtime-library/reference/clearerr.md), [clearerr_s](../c-runtime-library/reference/clearerr-s.md)|Effacer un indicateur d'erreur de flux|
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|Fermer un flux|
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|Fermer tous les flux ouverts sauf **stdin**, **stdout** et **stderr**|
|[_fdopen, wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Associer un flux au descripteur de fichier d'un fichier ouvert|
|[feof](../c-runtime-library/reference/feof.md)|Tester la fin de fichier sur un flux|
|[ferror](../c-runtime-library/reference/ferror.md)|Tester la présence d'erreur sur un flux|
|[fflush](../c-runtime-library/reference/fflush.md)|Vider un flux dans une mémoire tampon ou un dispositif de stockage|
|[fgetc, fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|Lire un caractère dans le flux (versions fonction de **getc** et **getwc**)|
|[_fgetchar, _fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|Lire un caractère à partir de **stdin** (versions fonction de **getchar** et **getwchar**)|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|Obtenir l'indicateur de position du flux|
|[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)|Lire une chaîne du flux|
|[_fileno](../c-runtime-library/reference/fileno.md)|Obtenir le descripteur de fichier associé au flux|
|[_flushall](../c-runtime-library/reference/flushall.md)|Vider tous les flux dans une mémoire tampon ou un dispositif de stockage|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Ouvrir un flux|
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|Écrire des données mises en forme dans le flux|
|[fputc, fputwc](../c-runtime-library/reference/fputc-fputwc.md)|Écrire un caractère dans un flux (versions fonction de **putc** et **putwc**)|
|[_fputchar, _fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|Écrire un caractère dans **stdout** (versions fonction de **putchar** et **putwchar**)|
|[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)|Écrire une chaîne dans le flux|
|[fread](../c-runtime-library/reference/fread.md)|Lire des données non mises en forme dans le flux|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Réaffecter le pointeur de flux **FILE** à un nouveau fichier ou périphérique|
|[fscanf, fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|Lire les données mises en forme du flux|
|[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|Déplacer la position d'un fichier vers un emplacement donné|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|Définir l'indicateur de position du flux|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Ouvrir le flux avec le partage de fichiers|
|[ftell, _ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|Obtenir la position actuelle d'un fichier|
|[fwrite](../c-runtime-library/reference/fwrite.md)|Écrire des éléments de données non mis en forme dans le flux|
|[getc, getwc](../c-runtime-library/reference/getc-getwc.md)|Lire un caractère dans le flux (versions macro de **fgetc** et **fgetwc**)|
|[getchar, getwchar](../c-runtime-library/reference/getc-getwc.md)|Lire un caractère à partir de **stdin** (versions macro de **fgetchar** et **fgetwchar**)|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|Retourner le nombre autorisé de fichiers ouverts simultanément au niveau de l'E/S du flux|
|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|Lire une ligne à partir de **stdin**|
|[_getw](../c-runtime-library/reference/getw.md)|Lire un **int** binaire dans le flux|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Écrire des données mises en forme dans **stdout**|
|[putc, putwc](../c-runtime-library/reference/putc-putwc.md)|Écrire un caractère dans un flux (versions macro de **fputc** et **fputwc**)|
|[putchar, putwchar](../c-runtime-library/reference/putc-putwc.md)|Écrire un caractère dans **stdout** (versions macro de **fputchar** et **fputwchar**)|
|[puts, _putws](../c-runtime-library/reference/puts-putws.md)|Écrire une ligne dans le flux|
|[_putw](../c-runtime-library/reference/putw.md)|Écrire un **int** binaire dans le flux|
|[rewind](../c-runtime-library/reference/rewind.md)|Déplacer la position d'un fichier au début du flux|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|Supprimer les fichiers temporaires créés par **tmpfile**|
|[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Lire les données mises en forme d’un **stdin**|
|[setbuf](../c-runtime-library/reference/setbuf.md)|Contrôler la mise en mémoire tampon du flux|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|Définir un nombre maximal de fichiers ouverts simultanément au niveau de l'E/S du flux|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|Contrôler la mise en mémoire tampon du flux et la taille de la mémoire tampon|
|[_snprintf, _snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|Écrire des données mises en forme de la longueur spécifiée dans une chaîne|
|[_snscanf, _snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|Lire les données mises en forme d'une longueur spécifiée dans le flux d'entrée standard|
|[sprintf, swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Écrire des données mises en forme dans une chaîne|
|[sscanf, swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Lire les données mises en forme d'une chaîne|
|[_tempnam, _wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|Générer un nom de fichier temporaire dans un répertoire donné|
|[tmpfile](../c-runtime-library/reference/tmpfile.md), [tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|Créer un fichier temporaire|
|[tmpnam, _wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md), [tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|Générer un nom de fichier temporaire|
|[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|Remettre un caractère dans le flux|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md), [_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|Écrire des données mises en forme dans la console|
|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|Écrire des données mises en forme dans le flux|
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), [vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|Écrire des données mises en forme dans **stdout**|
|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Écrire des données mises en forme de la longueur spécifiée dans la mémoire tampon|
|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|Écrire des données mises en forme dans la mémoire tampon|

Quand un programme lance l’exécution, le code de démarrage ouvre automatiquement plusieurs flux : une entrée standard (désignée par **stdin**), une sortie standard (désignée par **stdout**) et une erreur standard (désignée par **stderr**). Par défaut, ces flux sont dirigés vers la console (clavier et écran). Utilisez **freopen** pour rediriger **stdin**, **stdout** ou **stderr** vers un fichier sur disque ou un périphérique.

Par défaut, les fichiers ouverts à l'aide des routines de flux sont mis en mémoire tampon. Les fonctions **stdout** et **stderr** sont vidées chaque fois qu’elles sont pleines ou, si vous écrivez dans un périphérique d’entrée-sortie de caractères, après chaque appel de bibliothèque. Si un programme se termine de façon anormale, il est possible que les mémoires tampons de sortie ne se vident pas, entraînant ainsi une perte de données. Utilisez **fflush** ou **_flushall** pour faire en sorte que la mémoire tampon associée à un fichier spécifié ou toutes les mémoires tampons soient vidées sur le système d’exploitation, qui peut mettre les données en cache avant de les écrire sur disque. La fonctionnalité de validation sur disque garantit que le contenu de mémoire tampon vidé n'est pas perdu en cas de défaillance du système.

Il existe deux façons de valider le contenu de mémoire tampon sur disque :

- Créer un lien avec le fichier COMMODE.OBJ pour définir un indicateur de validation global. Le paramètre par défaut de l’indicateur global est **n**, pour « no-commit » (pas de validation).

- Définir l’indicateur de mode sur **c** avec **fopen** ou **_fdopen**.

Le comportement d’un fichier spécifiquement ouvert avec l’indicateur **c** ou **n** varie en fonction de cet indicateur, quel que soit l’indicateur de validation global (« commit »/« no-commit »).

Si votre programme ne ferme pas explicitement un flux, le flux est fermé automatiquement quand le programme se termine. Cependant, vous devez fermer un flux une fois que le programme en a terminé avec celui-ci, car le nombre de flux pouvant être ouverts simultanément est limité. Pour plus d'informations sur cette limite, consultez [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) .

Une entrée ne peut suivre directement une sortie qu’à condition de faire un appel intermédiaire à **fflush** ou à une fonction de positionnement de fichier (**fseek**, **fsetpos** ou **rewind**). Une sortie peut suivre une entrée sans appel intermédiaire à une fonction de positionnement de fichier si l'opération d'entrée rencontre la fin du fichier.

## <a name="see-also"></a>Voir aussi

[Entrée et sortie](../c-runtime-library/input-and-output.md)<br/>
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
