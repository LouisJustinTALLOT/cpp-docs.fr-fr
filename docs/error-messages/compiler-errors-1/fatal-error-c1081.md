---
title: Erreur irrécupérable C1081 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b34f2f19a0bb8770ea9292fef120c415c0fb255a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060526"
---
# <a name="fatal-error-c1081"></a>Erreur irrécupérable C1081

'symbol' : nom de fichier trop long

La longueur d’un chemin d’accès de fichier dépasse `_MAX_PATH` (défini par STDLIB.h à 260 caractères). Raccourcissez le nom du fichier.

Si vous appelez CL.exe avec un nom de fichier court, le compilateur peut-être générer un chemin d’accès complet. Par exemple, `cl -c myfile.cpp` peut entraîner le compilateur à générer :

```
D:\<very-long-directory-path>\myfile.cpp
```