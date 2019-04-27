---
title: Erreur irrécupérable C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: f3c9f9bde5da7fb120accbb9a8d72e5715ab9d2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229417"
---
# <a name="fatal-error-c1081"></a>Erreur irrécupérable C1081

'symbol' : nom de fichier trop long

La longueur d’un chemin d’accès de fichier dépasse `_MAX_PATH` (défini par STDLIB.h à 260 caractères). Raccourcissez le nom du fichier.

Si vous appelez CL.exe avec un nom de fichier court, le compilateur peut-être générer un chemin d’accès complet. Par exemple, `cl -c myfile.cpp` peut entraîner le compilateur à générer :

```
D:\<very-long-directory-path>\myfile.cpp
```