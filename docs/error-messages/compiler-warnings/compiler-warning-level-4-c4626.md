---
title: Compilateur avertissement (niveau 4) C4626 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4626
dev_langs:
- C++
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e43aa93a2f40d97ef3db5c2f556b04e84512724
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295134"
---
# <a name="compiler-warning-level-4-c4626"></a>Avertissement du compilateur (niveau 4) C4626
'classe dérivée' : l'opérateur d'assignation a été défini de manière implicite comme supprimé car un opérateur d'assignation de la classe de base est inaccessible ou supprimé  
  
 Un opérateur d'assignation a été supprimé ou n'était pas accessible dans une classe de base, et il n'a donc pas été généré pour une classe dérivée. Toute tentative pour assigner des objets de ce type provoquera une erreur du compilateur.  
  
 Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.  
  
 L'exemple suivant génère l'avertissement C4626 et montre comment le corriger :  
  
```  
// C4626  
// compile with: /W4  
#pragma warning(default : 4626)  
class B  
{  
// public:  
   B& operator = (const B&)  
   {  
      return *this;  
   }  
};  
  
class D : public B  
{  
  
}; // C4626 - to fix, make B's copy constructor public  
  
int main()  
{  
   D m;  
   D n;  
   // m = n;   // this line will cause an error  
}  
```