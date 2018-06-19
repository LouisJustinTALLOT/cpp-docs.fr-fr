---
title: vtordisp | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 502425728fcd97d2ae8d2efe406dc73370de1272
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841770"
---
# <a name="vtordisp"></a>vtordisp
**Spécifique à C++**  
  
 Contrôle l'ajout du membre de déplacement de construction/destruction vtordisp masqué.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#pragma vtordisp([push,] n)  
#pragma vtordisp(pop)  
#pragma vtordisp()  
#pragma vtordisp([push,] {on | off})  
```  
  
#### <a name="parameters"></a>Paramètres  
 `push`  
 Pousse le paramètre vtordisp actuel sur la pile interne du compilateur et affecte la valeur `n` au nouveau paramètre vtordisp.  Si la valeur `n` n'est pas spécifiée, le paramètre vtordisp actuel n'est pas modifié.  
  
 `pop`  
 Supprime l'enregistrement supérieur de la pile interne du compilateur et rétablit la valeur supprimée du paramètre vtordisp.  
  
 `n`  
 Spécifie la nouvelle valeur du paramètre vtordisp. Les valeurs possibles sont 0, 1 et 2, qui correspondent aux options /vd0, /vd1 et /vd2 du compilateur. Pour plus d’informations, consultez [/vd (désactiver les déplacements de Construction)](../build/reference/vd-disable-construction-displacements.md).  
  
 `on`  
 Équivalent à `#pragma vtordisp(1)`.  
  
 `off`  
 Équivalent à `#pragma vtordisp(0)`.  
  
## <a name="remarks"></a>Notes  
 Le pragma `vtordisp` peut s'appliquer uniquement à du code qui utilise des bases virtuelles. Si une classe dérivée remplace une fonction virtuelle qu'elle hérite d'une classe de base virtuelle et si un constructeur ou un destructeur pour la classe dérivée appelle cette fonction à l'aide d'un pointeur vers la classe de base virtuelle, le compilateur peut introduire des champs `vtordisp` masqués supplémentaires dans les classes dotées de bases virtuelles.  
  
 Le pragma `vtordisp` affecte la disposition des classes qui le suivent. Les options /vd0, /vd1 et /vd2 spécifient le même comportement pour les modules complets. La spécification de `0` ou `off` supprime les membres `vtordisp` masqués. Désactivez `vtordisp` seulement s'il n'est pas possible que les constructeurs et les destructeurs de la classe appellent des fonctions virtuelles sur l'objet vers lequel pointe le pointeur `this`.  
  
 La spécification de `1` ou `on` (valeur par défaut) active les membres `vtordisp` masqués là où ils sont nécessaires.  
  
 Spécification de `2` permet le texte masqué `vtordisp` membres pour toutes les bases virtuelles avec des fonctions virtuelles.  `vtordisp(2)` peut être nécessaire de garantir des performances correctes `dynamic_cast` sur un objet partiellement construit. Pour plus d’informations, consultez [l’avertissement du compilateur (niveau 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).  
  
 `#pragma vtordisp()`, sans argument, rétablit la valeur initiale du paramètre vtordisp.  
  
```  
#pragma vtordisp(push, 2)  
class GetReal : virtual public VBase { ... };  
#pragma vtordisp(pop)  
```  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)