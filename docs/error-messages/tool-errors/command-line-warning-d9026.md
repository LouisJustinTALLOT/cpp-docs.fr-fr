---
title: Avertissement de ligne de commande D9026 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2d99573ee46c51178cc2fe995fa0f526b800f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299836"
---
# <a name="command-line-warning-d9026"></a>Avertissement de ligne de commande D9026
options s’appliquent à toute ligne de commande  
  
 Une option a été spécifiée sur une commande après qu’un nom de fichier a été spécifié. L’option a été appliquée au fichier qui l’ont précédé.  
  
 Par exemple, dans la commande  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 le fichier VERDI.c qui est compilé à l’aide de l’option/G5, pas la valeur par défaut/G4.  
  
 Ce comportement est différent de celui des versions précédentes, ce qui est appliqué uniquement les options spécifiées avant le nom de fichier, qui résulte de VERDI.c par qui est compilé à l’aide de/G4 et Puccini.c par qui est compilé à l’aide / G5.