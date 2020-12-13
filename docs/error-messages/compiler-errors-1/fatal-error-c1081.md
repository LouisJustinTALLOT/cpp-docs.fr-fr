---
description: 'En savoir plus sur : erreur irrécupérable C1081'
title: Erreur irrécupérable C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: 97e1070cb24a70750e9c7d9f78a3860b26a7831a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330693"
---
# <a name="fatal-error-c1081"></a>Erreur irrécupérable C1081

'Symbol' : nom de fichier trop long

La longueur d’un chemin d’accès de fichier dépasse `_MAX_PATH` (définie par stdlib. h sous la forme de 260 caractères). Raccourcissez le nom du fichier.

Si vous appelez CL.exe avec un nom de fichier Short, le compilateur peut avoir besoin de générer un chemin d’accès complet. Par exemple, `cl -c myfile.cpp` peut provoquer la génération par le compilateur :

```
D:\<very-long-directory-path>\myfile.cpp
```
