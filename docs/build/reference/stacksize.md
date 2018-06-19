---
title: STACKSIZE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2093762b3c6f21d319c53a85da5ec5b430a1fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376245"
---
# <a name="stacksize"></a>STACKSIZE
Définit la taille de la pile, en octets.  
  
```  
STACKSIZE reserve[,commit]  
```  
  
## <a name="remarks"></a>Notes  
 Pour définir la pile d’une manière équivalente est avec le [Allocations de la pile](../../build/reference/stack-stack-allocations.md) (/Stack) option. Consultez la documentation sur cette option pour plus d’informations la *réserver* et `commit` arguments.  
  
 Cette option a aucun effet sur les DLL.  
  
## <a name="see-also"></a>Voir aussi  
 [Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)