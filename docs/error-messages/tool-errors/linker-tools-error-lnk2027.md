---
title: Erreur LNK2027 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156310a0d21651b9fd2ee6002ace419db4996681
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301370"
---
# <a name="linker-tools-error-lnk2027"></a>Erreur des outils Éditeur de liens LNK2027
module non résolue référence 'module'  
  
 Un fichier passé à l’éditeur de liens a une dépendance sur un module qui n’était ni spécifié avec **/ASSEMBLYMODULE** ni passé directement à l’éditeur de liens.  
  
 Pour résoudre l’erreur LNK2027, effectuez l’une des opérations suivantes :  
  
-   Ne passez pas à l’éditeur de liens du fichier qui comporte la dépendance de module.  
  
-   Spécifiez le module avec **/ASSEMBLYMODULE**.  
  
-   Si le module est un fichier .netmodule sécurisé, passez-le directement à l’éditeur de liens.  
  
 Pour plus d’informations, consultez [/ASSEMBLYMODULE (ajouter un Module MSIL à l’Assembly)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) et [fichiers .netmodule en tant qu’entrée de l’éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).