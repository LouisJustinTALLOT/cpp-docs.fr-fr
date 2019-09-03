---
title: vtordisp, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: 3c676ab2bfee1b6cf3caff3ab456a4f23f2744c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216480"
---
# <a name="vtordisp-pragma"></a>vtordisp, pragma

**C++Plus**

Contrôle l’ajout du membre de `vtordisp` déplacement de construction/destruction masqué.

## <a name="syntax"></a>Syntaxe

> **#pragma vtordisp (** [ **push,** ] *n* **)** \
> **#pragma vtordisp (POP)** \
> **#pragma vtordisp ()** \
> **#pragma vtordisp (** [ **push,** ] { **on** | **off** } **)**

### <a name="parameters"></a>Paramètres

**souleve**\
Exécute un push du `vtordisp` paramètre actuel sur la pile interne du compilateur et définit le `vtordisp` nouveau paramètre sur *n*.  Si *n* n’est pas spécifié, `vtordisp` le paramètre actuel est inchangé.

**roulant**\
Supprime l’enregistrement supérieur de la pile interne du compilateur et restaure le `vtordisp` paramètre à la valeur supprimée.

*n*\
Spécifie la nouvelle valeur `vtordisp` du paramètre. Les valeurs possibles sont 0, 1 ou 2, ce `/vd0`qui correspond aux options de compilateur, `/vd1`et `/vd2` . Pour plus d’informations, consultez [/VD (désactiver les déplacements de construction)](../build/reference/vd-disable-construction-displacements.md).

**sur**\
Équivalent à `#pragma vtordisp(1)`.

**préférable**\
Équivalent à `#pragma vtordisp(0)`.

## <a name="remarks"></a>Notes

Le pragma **vtordisp** s’applique uniquement au code qui utilise des bases virtuelles. Si une classe dérivée remplace une fonction virtuelle qu'elle hérite d'une classe de base virtuelle et si un constructeur ou un destructeur pour la classe dérivée appelle cette fonction à l'aide d'un pointeur vers la classe de base virtuelle, le compilateur peut introduire des champs `vtordisp` masqués supplémentaires dans les classes dotées de bases virtuelles.

Le pragma **vtordisp** affecte la disposition des classes qui le suivent. Les `/vd0`options `/vd1`, et`/vd2` spécifient le même comportement pour les modules complets. Si vous spécifiez la valeur 0 ou `vtordisp` **off** , les membres masqués sont supprimés. Désactivez **vtordisp** uniquement s’il n’est pas possible que les constructeurs et les destructeurs de la classe appellent des fonctions virtuelles sur l' `this` objet vers lequel pointe le pointeur.

Si vous spécifiez 1 ou **on**, la valeur par `vtordisp` défaut active les membres masqués là où ils sont nécessaires.

La spécification de 2 active `vtordisp` les membres masqués pour toutes les bases virtuelles avec des fonctions virtuelles.  `#pragma vtordisp(2)`peut être nécessaire pour garantir des performances correctes de **dynamic_cast** sur un objet partiellement construit. Pour plus d’informations, consultez [Avertissement du compilateur (niveau 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).

`#pragma vtordisp()`, sans argument, rétablit la valeur `vtordisp` initiale du paramètre.

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
