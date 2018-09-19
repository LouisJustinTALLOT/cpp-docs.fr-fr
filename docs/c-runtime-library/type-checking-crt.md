---
title: Contrôle de type (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.types
dev_langs:
- C++
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29cc7366385c187b1324f4d7e6b896a19ac86074
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041270"
---
# <a name="type-checking-crt"></a>Contrôle de type (CRT)

Le compilateur effectue une vérification de type limitée sur les fonctions qui peuvent prendre un nombre variable d’arguments, comme suit :

|Appel de fonction |Arguments avec vérification de type|
|-------------------|-----------------------------|
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|Premier argument (chaîne de format)|
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|Deux premiers arguments (fichier ou mémoire tampon et format de chaîne)|
|`_snprintf_s`|Trois premiers arguments (fichier ou mémoire tampon, nombre et chaîne de format)|
|`_open`|Deux premiers arguments (chemin d’accès et indicateur `_open`)|
|`_sopen_s`|Trois premiers arguments (chemin d’accès, indicateur `_open` et mode de partage)|
|`_execl`, `_execle`, `_execlp`, `_execlpe`|Deux premiers arguments (chemin d’accès et premier pointeur d’argument)|
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|Trois premiers arguments (indicateur de mode, chemin d’accès et premier pointeur d’argument)|

Le compilateur effectue la même vérification de type limitée sur les équivalents à caractères larges de ces fonctions.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)