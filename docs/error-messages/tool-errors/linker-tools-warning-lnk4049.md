---
title: Avertissement LNK4049 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4049
dev_langs:
- C++
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b50dadc9c160ac8902cedcd60c954b565dce6e24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302371"
---
# <a name="linker-tools-warning-lnk4049"></a>Avertissement des outils Éditeur de liens LNK4049
le symbole 'symbole' importé défini localement  
  
 Le symbole a été à la fois exporté à partir d’et importé dans le programme.  
  
 Cet avertissement est généré par l’éditeur de liens lorsque vous déclarez un symbole à l’aide de la `__declspec(dllexport)` classe de stockage d’attributs dans un fichier objet et y fait référence à l’aide de la `__declspec(dllimport)` attribut dans un autre.  
  
 Avertissement LNK4049 est une version plus générale de [avertissement d’outils de l’éditeur de liens LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md). L’éditeur de liens génère l’avertissement LNK4049 lorsqu’il ne peut pas déterminer de quelle fonction le symbole importé a été référencé.  
  
 Les cas courants où LNK4049 est généré au lieu de LNK4217 sont :  
  
-   Exécution d’une liaison incrémentielle à l’aide de la [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) option.  
  
-   Exécution d’optimisation de la totalité du programme à l’aide de la [LTCG](../../build/reference/ltcg-link-time-code-generation.md) option.  
  
 Pour résoudre l’erreur LNK4049, essayez l’une des opérations suivantes :  
  
-   Supprimer le `__declspec(dllimport)` déclaration de la déclaration anticipée du symbole qui a déclenché LNK4049 de nom. Vous pouvez rechercher les symboles au sein d’une image binaire à l’aide de la **DUMPBIN** utilitaire. Le **DUMPBIN/symboles** commutateur affiche la table de symboles COFF de l’image. Pour plus d’informations sur la **DUMPBIN** utilitaire, consultez [Référence DUMPBIN](../../build/reference/dumpbin-reference.md).  
  
-   Désactiver temporairement la liaison incrémentielle et l’optimisation de la totalité du programme. Recompiler l’application génère l’avertissement LNK4217, lequel inclut le nom de la fonction à partir de laquelle le symbole importé a été référencé. Supprimer le `__declspec(dllimport)` déclaration de symbole importé et d’activer la liaison incrémentielle ou de l’optimisation de la totalité du programme comme requis.  
  
 Bien que le code final généré se comporte correctement, le code généré pour appeler la fonction importée est moins efficace que l’appel direct de la fonction. Cet avertissement n’apparaît pas lorsque vous compilez à l’aide de l’option [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Pour plus d’informations sur Importer et exporter des déclarations de données, consultez [dllexport, dllimport](../../cpp/dllexport-dllimport.md).  
  
## <a name="example"></a>Exemple  
 Liaison des deux modules suivants génère LNK4049. Le premier module génère un fichier objet contenant une seule fonction exportée.  
  
```  
// LNK4049a.cpp  
// compile with: /c  
  
__declspec(dllexport) int func()   
{  
   return 3;  
}  
```  
  
## <a name="example"></a>Exemple  
 Le deuxième module génère un fichier objet qui contient une déclaration anticipée à la fonction exportée dans le premier module, ainsi que d’un appel à cette fonction à l’intérieur de la `main` (fonction). Liaison de ce module avec le premier module génère LNK4049. Suppression de la `__declspec(dllimport)` déclaration peut résoudre l’avertissement.  
  
```  
// LNK4049b.cpp  
// compile with: /link /WX /LTCG LNK4049a.obj  
// LNK4049 expected  
  
__declspec(dllimport) int func();  
// try the following line instead  
// int func();  
  
int main()  
{  
   return func();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de l’éditeur de liens LNK4217 d’avertissement](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)