---
title: Corps de fonction ou Variable manquant | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54e2b8c5831eb6d487cf530df1b733b73580cbb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316723"
---
# <a name="missing-function-body-or-variable"></a>Corps de fonction ou variable manquant
Avec seulement un prototype de fonction, le compilateur peut poursuivre sans erreur, mais l’éditeur de liens ne peut pas résoudre un appel à une adresse, car il n’existe aucun code de fonction ou un espace réservé pour la variable. Vous ne verrez pas cette erreur avant la création d’un appel à la fonction de l’éditeur de liens doit être résolue.  
  
## <a name="example"></a>Exemple  
 L’appel de fonction dans main entraîne l’erreur LNK2019, car le prototype permet au compilateur de considérer que la fonction existe.  L’éditeur de liens recherche que ce n’est pas.  
  
```  
// LNK2019_MFBV.cpp  
// LNK2019 expected  
void DoSomething(void);  
int main() {  
   DoSomething();  
}  
```  
  
## <a name="example"></a>Exemple  
 En C++, assurez-vous que vous incluez l’implémentation d’une fonction spécifique pour une classe et pas seulement un prototype dans la définition de classe. Si vous définissez la classe en dehors du fichier d’en-tête, veillez à inclure le nom de classe avant la fonction (`Classname::memberfunction`).  
  
```  
// LNK2019_MFBV_2.cpp  
// LNK2019 expected  
struct A {  
   static void Test();  
};  
  
// Should be void A::Test() {}  
void Test() {}  
  
int main() {  
   A AObject;  
   AObject.Test();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Erreur des outils Éditeur de liens LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)