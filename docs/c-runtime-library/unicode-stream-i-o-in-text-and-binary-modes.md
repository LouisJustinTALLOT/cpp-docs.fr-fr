---
title: E/S de flux Unicode en mode texte et binaire | Microsoft Docs
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
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b89ff3fc752901e9b3cf30c305110b387dc04562
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409051"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>E/S de flux Unicode en modes texte et binaire

Quand une routine d’E/S de flux Unicode (comme **fwprintf**, **fwscanf**, **fgetwc**, **fputwc**, **fgetws** ou **fputws**) fonctionne sur un fichier ouvert en mode texte (mode par défaut), deux types de conversions de caractères se produisent :

- Conversion Unicode vers MBCS ou MBCS vers Unicode. Quand une fonction d’E/S de flux Unicode s’exécute en mode texte, le flux source ou de destination est supposé être une séquence de caractères multi-octets. Par conséquent, les fonctions d’entrée de flux Unicode convertissent les caractères multioctets en caractères larges (comme après un appel à la fonction **mbtowc**). Pour la même raison, les fonctions de flux de sortie Unicode convertissent les caractères larges en caractères multioctets (comme après un appel à la fonction **wctomb**).

- Traduction Retour chariot - Saut de ligne (CR-LF). Cette traduction se produit avant la conversion MBCS - Unicode (pour les fonctions d’entrée de flux Unicode) et après la conversion Unicode - MBCS (pour les fonctions de sortie de flux Unicode). Au cours de l’entrée, chaque combinaison Retour chariot - Saut de ligne est traduite en caractère de saut de ligne unique. Au cours de la sortie, chaque caractère de saut de ligne est traduit en combinaison Retour chariot - Saut de ligne.

Toutefois, quand une fonction d’E/S de flux Unicode s’exécute en mode binaire, le fichier est supposé être Unicode et aucune traduction CR-LF ou conversion de caractère ne se produisent au cours de l’entrée ou de la sortie. Utilisez l’instruction _setmode(_fileno( stdin ), _O_BINARY ); pour utiliser correctement wcin dans un fichier texte UNICODE.

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Entrée et sortie](../c-runtime-library/input-and-output.md)<br/>
