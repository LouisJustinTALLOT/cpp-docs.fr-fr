---
title: Avertissement de ligne de commande D9027 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfe2493290c4e4cc5b744136b8e7036c6559220a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301448"
---
# <a name="command-line-warning-d9027"></a>Avertissement de ligne de commande D9027
fichier source '\<nom_fichier >' ignoré  
  
 CL.exe a ignoré le fichier source d’entrée.  
  
 Cet avertissement peut être provoqué par un espace entre l’option /Fo et un nom de fichier de sortie sur une ligne de commande avec l’option /c. Par exemple :  
  
```  
cl /c /Fo output.obj input.c   
```  
  
 Étant donné qu’un espace entre /Fo et `output.obj`, CL.exe prend `output.obj` en tant que le nom du fichier d’entrée. Pour résoudre le problème, supprimez l’espace :  
  
```  
cl /c /Fooutput.obj input.c   
```