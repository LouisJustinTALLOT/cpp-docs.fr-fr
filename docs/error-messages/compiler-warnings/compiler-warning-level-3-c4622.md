---
title: Compilateur avertissement (niveau 3) C4622 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4622
dev_langs:
- C++
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b82e87f37b50b8df727d043889cb35ca02d3f78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291539"
---
# <a name="compiler-warning-level-3-c4622"></a>Avertissement du compilateur (niveau 3) C4622
Remplacement des informations de débogage formées lors de la création de l’en-tête précompilé du fichier objet : 'fichier'  
  
 Les informations CodeView dans le fichier spécifié ont été perdues lorsqu’il a été compilé avec l’option [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (utiliser des en-têtes précompilés).  
  
 Renommez le fichier objet (à l’aide de [/Fo](../../build/reference/fo-object-file-name.md)) lors de la création ou de l’utilisation du fichier d’en-tête précompilé et établissez une liaison avec le nouveau fichier objet.