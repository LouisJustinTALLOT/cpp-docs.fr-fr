---
title: vtordisp
ms.date: 10/18/2018
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: 075f00ad8a4071af57014638707503847b58756d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557181"
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

### <a name="parameters"></a>Paramètres

*push*<br/>
Envoie le paramètre vtordisp actuel sur la pile interne du compilateur et affecte le nouveau paramètre vtordisp *n*.  Si *n* n’est pas spécifié, le paramètre vtordisp actuel n’est pas modifié.

*pop*<br/>
Supprime l'enregistrement supérieur de la pile interne du compilateur et rétablit la valeur supprimée du paramètre vtordisp.

*n*<br/>
Spécifie la nouvelle valeur du paramètre vtordisp. Les valeurs possibles sont 0, 1 ou 2, correspondant à la `/vd0`, `/vd1`, et `/vd2` options du compilateur. Pour plus d’informations, consultez [/vd (désactiver les déplacements de Construction)](../build/reference/vd-disable-construction-displacements.md).

*on*<br/>
Équivalent à `#pragma vtordisp(1)`.

*Hors tension*<br/>
Équivalent à `#pragma vtordisp(0)`.

## <a name="remarks"></a>Notes

Le **vtordisp** pragma s’applique uniquement au code qui utilise des bases virtuelles. Si une classe dérivée remplace une fonction virtuelle qu’elle hérite d’une classe de base virtuelle, et si un constructeur ou un destructeur pour la classe dérivée appelle cette fonction à l’aide d’un pointeur vers la classe de base virtuelle, le compilateur peut introduire masquéssupplémentaires**vtordisp** les champs dans des classes avec bases virtuelles.

Le **vtordisp** pragma affecte la disposition des classes qui le suivent. Le `/vd0`, `/vd1`, et `/vd2` options spécifient le même comportement pour les modules complets. Spécification de 0 ou *hors* supprime le texte masqué **vtordisp** membres. Désactiver **vtordisp** uniquement s’il existe aucune possibilité de la classe constructeurs et destructeurs appellent virtuels ne fonctionne sur l’objet vers lequel pointé le **cela** pointeur.

Spécification de 1 ou *sur*, permet à la valeur par défaut, le texte masqué **vtordisp** membres là où ils sont nécessaires.

En spécifiant 2 permet le texte masqué **vtordisp** membres pour toutes les bases virtuelles avec des fonctions virtuelles.  `vtordisp(2)` peut être nécessaire de garantir des performances correctes de **dynamic_cast** sur un objet partiellement construit. Pour plus d’informations, consultez [Avertissement du compilateur (niveau 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).

`#pragma vtordisp()`, sans argument, rétablit la valeur initiale du paramètre vtordisp.

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)