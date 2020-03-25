---
title: Erreur irrécupérable C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: b8630a26d14c68a5f1abe45bb0b8d0141d0dedbb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204189"
---
# <a name="fatal-error-c1081"></a>Erreur irrécupérable C1081

'Symbol' : nom de fichier trop long

La longueur d’un nom de chemin d’accès au fichier dépasse `_MAX_PATH` (définie par STDLIB. h sous la forme de 260 caractères). Raccourcissez le nom du fichier.

Si vous appelez CL. exe avec un nom de fichier Short, le compilateur peut avoir besoin de générer un nom de chemin d’accès complet. Par exemple, `cl -c myfile.cpp` peut provoquer la génération par le compilateur :

```
D:\<very-long-directory-path>\myfile.cpp
```
