---
title: E/S de console et de port | Microsoft Docs
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
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e0750a2c0b8747da432efd9fc465b83e01a490
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018273"
---
# <a name="console-and-port-io"></a>Console et port E/S

Ces routines lisent et écrivent sur votre console ou sur le port spécifié. Les routines d’E/S de console ne sont pas compatibles avec les E/S de flux ou les routines de bibliothèque d’E/S de bas niveau. La console ou le port n’a pas à être ouvert ou fermé avant l’exécution des E/S, il n’y a donc pas de routines ouvertes ou fermées dans cette catégorie. Dans les systèmes d’exploitation Windows, la sortie de ces fonctions est toujours dirigée vers la console et ne peut pas être redirigée.

## <a name="console-and-port-io-routines"></a>Routines d'E/S de console et de port

|Routine|Utilisez|
|-------------|---------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md), [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Lire une chaîne de la console|
|[_cprintf, _cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|Écrire des données mises en forme dans la console|
|[_cputs](../c-runtime-library/reference/cputs-cputws.md)|Écrire une chaîne dans la console|
|[_cscanf, _cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|Lire les données mises en forme de la console|
|[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)|Lire un caractère à partir de la console|
|[_getche, _getwche](../c-runtime-library/reference/getch-getwch.md)|Lire un caractère à partir de la console et l’afficher à l’écran|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|Lire un octet à partir du port d’E/S spécifié|
|[_inpd](../c-runtime-library/inp-inpw-inpd.md)|Lire un mot double à partir du port d’E/S spécifié|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|Lire un mot de 2 octets à partir du port d’E/S spécifié|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|Vérifier la séquence de touches sur la console ; utiliser avant d’essayer de lire à partir de la console|
|[_outp](../c-runtime-library/outp-outpw-outpd.md)|Écrit un octet sur le port d’E/S spécifié|
|[_outpd](../c-runtime-library/outp-outpw-outpd.md)|Écrire un mot double sur le port d’E/S spécifié|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|Écrire le mot sur le port d’E/S spécifié|
|[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)|Écrire un caractère dans la console|
|[_ungetch, _ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|Applique « unget » au dernier caractère lu à partir de la console afin qu’il devienne le caractère lu suivant|

## <a name="see-also"></a>Voir aussi

[Entrée et sortie](../c-runtime-library/input-and-output.md)<br/>
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>