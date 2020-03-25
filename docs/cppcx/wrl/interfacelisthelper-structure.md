---
title: InterfaceListHelper (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: 1a7b4c19bbcdd4161e9078274f18f96a48f9e7d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213848"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename T0,
    typename T1 = Nil,
    typename T2 = Nil,
    typename T3 = Nil,
    typename T4 = Nil,
    typename T5 = Nil,
    typename T6 = Nil,
    typename T7 = Nil,
    typename T8 = Nil,
    typename T9 = Nil
>
struct InterfaceListHelper;

template <typename T0>
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;
```

### <a name="parameters"></a>Paramètres

*T0*<br/>
Paramètre de modèle 0, ce qui est requis.

*T1*<br/>
Paramètre de modèle 1, qui, par défaut, n’est pas spécifié.

*T2*<br/>
Paramètre de modèle 2, qui, par défaut, n’est pas spécifié. Troisième paramètre de modèle.

*T3*<br/>
Paramètre de modèle 3, qui, par défaut, n’est pas spécifié.

*T4*<br/>
Paramètre de modèle 4, qui, par défaut, n’est pas spécifié.

*T5*<br/>
Paramètre de modèle 5, qui, par défaut, n’est pas spécifié.

*T6*<br/>
Paramètre de modèle 6, qui, par défaut, n’est pas spécifié.

*T7*<br/>
Paramètre de modèle 7, qui, par défaut, n’est pas spécifié.

*T8*<br/>
Paramètre de modèle 8, qui, par défaut, n’est pas spécifié.

*T9*<br/>
Paramètre de modèle 9, qui, par défaut, n’est pas spécifié.

## <a name="remarks"></a>Notes

Génère un type de `InterfaceList` en appliquant de manière récursive les arguments de paramètre de modèle spécifiés.

Le modèle **interfacelisthelper (** utilise le paramètre de modèle *T0* pour définir le premier membre de données dans une structure `InterfaceList`, puis applique de manière récursive le modèle **interfacelisthelper (** aux paramètres de modèle restants. **Interfacelisthelper (** s’arrête lorsqu’il n’y a aucun paramètre de modèle restant.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`TypeT`|Synonyme du type Interfacelist (.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InterfaceListHelper`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)
