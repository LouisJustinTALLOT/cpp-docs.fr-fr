---
title: E/S de flux Unicode en modes texte et binaire
ms.date: 11/04/2016
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
ms.openlocfilehash: b41818bbb625a8c875771e86e3d82b74f4291e9f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444502"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>E/S de flux Unicode en modes texte et binaire

Quand une routine d’E/S de flux Unicode (comme **fwprintf**, **fwscanf**, **fgetwc**, **fputwc**, **fgetws** ou **fputws**) fonctionne sur un fichier ouvert en mode texte (mode par défaut), deux types de conversions de caractères se produisent :

- Conversion Unicode vers MBCS ou MBCS vers Unicode. Quand une fonction d’E/S de flux Unicode s’exécute en mode texte, le flux source ou de destination est supposé être une séquence de caractères multi-octets. Par conséquent, les fonctions d’entrée de flux Unicode convertissent les caractères multioctets en caractères larges (comme après un appel à la fonction **mbtowc**). Pour la même raison, les fonctions de flux de sortie Unicode convertissent les caractères larges en caractères multioctets (comme après un appel à la fonction **wctomb**).

- Traduction Retour chariot - Saut de ligne (CR-LF). Cette traduction se produit avant la conversion MBCS - Unicode (pour les fonctions d’entrée de flux Unicode) et après la conversion Unicode - MBCS (pour les fonctions de sortie de flux Unicode). Au cours de l’entrée, chaque combinaison Retour chariot - Saut de ligne est traduite en un seul caractère de saut de ligne. Au cours de la sortie, chaque caractère de saut de ligne est traduit en combinaison Retour chariot - Saut de ligne.

Toutefois, quand une fonction d’E/S de flux Unicode s’exécute en mode binaire, le fichier est supposé être Unicode et aucune traduction CR-LF ou conversion de caractère ne se produisent au cours de l’entrée ou de la sortie. Utilisez l’instruction `_setmode( _fileno( stdin ), _O_BINARY );` pour utiliser `wcin` correctement sur un fichier texte Unicode.

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Entrée et sortie](../c-runtime-library/input-and-output.md)<br/>
