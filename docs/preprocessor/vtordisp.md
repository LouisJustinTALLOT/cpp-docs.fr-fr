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
ms.openlocfilehash: a6ffc5c0323389d812e659ff68555a8c8c993126
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219363"
---
# <a name="vtordisp-pragma"></a>vtordisp, pragma

**Section spécifique à C++**

Contrôle l’ajout du membre de `vtordisp` déplacement de construction/destruction masqué.

## <a name="syntax"></a>Syntaxe

> **#pragma vtordisp (** [ **push,** ] *n* **)**\
> **#pragma vtordisp (POP)**\
> **#pragma vtordisp ()**\
> **#pragma vtordisp (** [ **push,** ] { **on**  |  **off** } **)**

### <a name="parameters"></a>Paramètres

**souleve**\
Exécute un push du `vtordisp` paramètre actuel sur la pile interne du compilateur et définit le nouveau `vtordisp` paramètre sur *n*.  Si *n* n’est pas spécifié, le `vtordisp` paramètre actuel est inchangé.

**roulant**\
Supprime l’enregistrement supérieur de la pile interne du compilateur et restaure le `vtordisp` paramètre à la valeur supprimée.

*n*\
Spécifie la nouvelle valeur du `vtordisp` paramètre. Les valeurs possibles sont 0, 1 ou 2, ce qui correspond aux `/vd0` `/vd1` options de compilateur, et `/vd2` . Pour plus d’informations, consultez [/VD (désactiver les déplacements de construction)](../build/reference/vd-disable-construction-displacements.md).

**sur**\
Équivaut à `#pragma vtordisp(1)`.

**préférable**\
Équivaut à `#pragma vtordisp(0)`.

## <a name="remarks"></a>Notes

Le pragma **vtordisp** s’applique uniquement au code qui utilise des bases virtuelles. Si une classe dérivée remplace une fonction virtuelle qu'elle hérite d'une classe de base virtuelle et si un constructeur ou un destructeur pour la classe dérivée appelle cette fonction à l'aide d'un pointeur vers la classe de base virtuelle, le compilateur peut introduire des champs `vtordisp` masqués supplémentaires dans les classes dotées de bases virtuelles.

Le pragma **vtordisp** affecte la disposition des classes qui le suivent. Les `/vd0` `/vd1` options, et `/vd2` spécifient le même comportement pour les modules complets. Si vous spécifiez la valeur 0 ou **off** , les membres masqués sont supprimés `vtordisp` . Désactivez **vtordisp** uniquement s’il n’est pas possible que les constructeurs et les destructeurs de la classe appellent des fonctions virtuelles sur l’objet vers lequel pointe le **`this`** pointeur.

Si vous spécifiez 1 ou **on**, la valeur par défaut active les membres masqués `vtordisp` là où ils sont nécessaires.

La spécification de 2 active les membres masqués `vtordisp` pour toutes les bases virtuelles avec des fonctions virtuelles.  `#pragma vtordisp(2)`peut être nécessaire pour garantir des performances correctes de **`dynamic_cast`** sur un objet partiellement construit. Pour plus d’informations, consultez [Avertissement du compilateur (niveau 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).

`#pragma vtordisp()`, sans argument, rétablit la valeur `vtordisp` initiale du paramètre.

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
