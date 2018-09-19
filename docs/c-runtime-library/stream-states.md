---
title: États des flux | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bdf4b351b05204fab11be2f5a0a1a8b7f71f462
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056350"
---
# <a name="stream-states"></a>États de flux

Les états valides et les transitions d’état d’un flux de données sont indiqués dans l’illustration suivante.

![Flux](../c-runtime-library/media/stream.gif "flux")

Chaque cercle indique un état stable. Chacune des lignes dénote une transition qui peut se produire à la suite d’un appel de fonction opérant sur le flux de données. Cinq groupes de fonctions peuvent entraîner des transitions d’état.

Les fonctions des trois premiers groupes sont déclarées dans \<stdio.h> :

- Fonctions de lecture d’octets : [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md), [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fread](../c-runtime-library/reference/fread.md), [fscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getc](../c-runtime-library/reference/getc-getwc.md), [getchar](../c-runtime-library/reference/getc-getwc.md), [gets](../c-runtime-library/gets-getws.md), [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), et [ungetc](../c-runtime-library/reference/ungetc-ungetwc.md)

- Fonctions d’écriture d’octets : [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputc](../c-runtime-library/reference/fputc-fputwc.md), [fputs](../c-runtime-library/reference/fputs-fputws.md), [fwrite](../c-runtime-library/reference/fwrite.md), [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [putc](../c-runtime-library/reference/putc-putwc.md), [putchar](../c-runtime-library/reference/putc-putwc.md), [puts](../c-runtime-library/reference/puts-putws.md), [vfprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) et [vprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)

- Fonctions de position : [fflush](../c-runtime-library/reference/fflush.md), [fseek](../c-runtime-library/reference/fseek-fseeki64.md), [fsetpos](../c-runtime-library/reference/fsetpos.md) et [rewind](../c-runtime-library/reference/rewind.md)

Les fonctions des deux autres groupes sont déclarées dans \<wchar.h> :

- Fonctions de lecture larges : [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getwc](../c-runtime-library/reference/getc-getwc.md), [getwchar](../c-runtime-library/reference/getc-getwc.md), [ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md), et [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),

- Fonctions d’écriture larges : [fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputwc](../c-runtime-library/reference/fputc-fputwc.md), [fputws](../c-runtime-library/reference/fputs-fputws.md), [putwc](../c-runtime-library/reference/putc-putwc.md), [putwchar](../c-runtime-library/reference/fputc-fputwc.md), [vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md) et [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),

Le diagramme d’état indique que vous devez appeler l’une des fonctions de position entre la plupart des opérations d’écriture et de lecture :

- Vous ne pouvez pas appeler une fonction de lecture si la dernière opération du flux est une opération d’écriture.

- Vous ne pouvez pas appeler une fonction d’écriture si la dernière opération du flux est une opération de lecture, sauf si l’opération de lecture a défini l’indicateur de fin de fichier.

Enfin, le diagramme d’état indique qu’une opération de position ne diminue jamais le nombre d’appels de fonctions valides qui peuvent suivre.

## <a name="see-also"></a>Voir aussi

[Fichiers et flux](../c-runtime-library/files-and-streams.md)