---
title: Compilateur avertissement (niveau 4) C4431 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4431
dev_langs:
- C++
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bb5a76a1ddf1f1104fe88511c9bf9bf88bf6602
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292254"
---
# <a name="compiler-warning-level-4-c4431"></a>Avertissement du compilateur (niveau 4) C4431
spécificateur de type manquant - int est pris en compte par défaut. Remarque : C ne prend plus en charge int par défaut  
  
 Cette erreur peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : Visual C++ ne crée plus identificateurs non typés en tant qu’int par défaut. Le type d’un identificateur doit être spécifié explicitement.  
  
 Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4431.  
  
```  
// C4431.c  
// compile with: /c /W4  
#pragma warning(default:4431)  
i;   // C4431  
int i;   // OK  
```