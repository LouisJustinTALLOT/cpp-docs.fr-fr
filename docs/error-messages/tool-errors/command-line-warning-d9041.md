---
title: Avertissement de ligne de commande D9041 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9041
dev_langs:
- C++
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c22573d26e09e14789f4cbd64d68f4082125c2b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298637"
---
# <a name="command-line-warning-d9041"></a>Avertissement de ligne de commande D9041
non valide 'valeur' pour '/ option' ; en supposant que 'value' ; Ajoutez ' /analyze ' aux options de ligne de commande lors de la spécification de cet avertissement  
  
 Un numéro d’avertissement de l’analyse du Code a été ajouté à la **/wd**, **/we**, **/wo**, ou **/wl** option de ligne de commande sans spécifier également le **/ analyze** option de ligne de commande. Pour corriger cette erreur, ajoutez le **/ analyze** option de ligne de commande, ou supprimez le numéro d’avertissement non valide approprié **Wn** option de ligne de commande.  
  
## <a name="example"></a>Exemple  
 L’exemple de ligne de commande suivant génère l’avertissement D9041 :  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 Pour résoudre l’avertissement, ajoutez le **/ analyze** option de ligne de commande. Si **/ analyze** est ne pas pris en charge sur votre version du compilateur, supprimez le numéro d’avertissement non valide à partir de la **/wd** option.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de ligne de commande D8000 à D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)