---
title: LNK2039 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 954ea12eb9b49c2bdf59b31a1ec2ec2e66c124ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302095"
---
# <a name="linker-tools-error-lnk2039"></a>Erreur des outils Éditeur de liens LNK2039
l’importation de la classe ref\<type >' qui est définie dans another.obj ; il doit être importée ou définie, mais pas les deux  
  
 La classe ref ' <`type`>' est importé dans le fichier .obj spécifié mais est également défini dans un autre fichier .obj. Cette condition peut entraîner la défaillance d’exécution ou tout autre comportement inattendu.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérifiez si «`type`' doit être défini dans l’autre fichier .obj et vérifier si elle doit être importé à partir du fichier .winmd.  
  
2.  Supprimer la définition ou l’importation.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)   
 [Erreur des outils Éditeur de liens LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)