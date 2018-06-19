---
title: Erreur irrécupérable C1081 | Documents Microsoft
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
ms.openlocfilehash: 4b5ea18ff3f2714d9621d4372cf541be2f9b225a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230520"
---
# <a name="fatal-error-c1081"></a>Erreur irrécupérable C1081
'symbole' : nom de fichier trop long  
  
 La longueur d’un chemin d’accès de fichier dépasse `_MAX_PATH` (défini par STDLIB.h à 260 caractères). Raccourcissez le nom du fichier.  
  
 Si vous appelez CL.exe avec un nom de fichier court, le compilateur devrez peut-être générer un chemin d’accès complet. Par exemple, `cl -c myfile.cpp` peut entraîner le compilateur à générer :  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```