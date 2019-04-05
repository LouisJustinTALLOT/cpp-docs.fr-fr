---
title: InterfaceListHelper (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: 03bfed00147daef22fe91e6f061ea6720834090f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025109"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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
Paramètre de modèle 0, ce qui est nécessaire.

*T1*<br/>
Paramètre de modèle 1, qui par défaut n’est pas spécifié.

*T2*<br/>
Paramètre de modèle 2, qui par défaut n’est pas spécifié. Le troisième paramètre de modèle.

*T3*<br/>
Paramètre de modèle 3, qui par défaut n’est pas spécifié.

*T4*<br/>
Paramètre de modèle 4, qui par défaut n’est pas spécifié.

*T5*<br/>
Paramètre de modèle 5, qui par défaut n’est pas spécifié.

*T6*<br/>
Paramètre de modèle 6, qui par défaut n’est pas spécifié.

*T7*<br/>
Paramètre de modèle 7, qui par défaut n’est pas spécifié.

*T8*<br/>
Paramètre de modèle 8, qui par défaut n’est pas spécifié.

*T9*<br/>
Paramètre de modèle 9, qui par défaut n’est pas spécifié.

## <a name="remarks"></a>Notes

Génère un `InterfaceList` type en appliquant les arguments de paramètre de modèle spécifié de manière récursive.

Le **InterfaceListHelper** modèle utilise le paramètre de modèle *T0* pour définir le premier membre de données dans un `InterfaceList` structure, puis de manière récursive s’applique le  **InterfaceListHelper** modèle pour les autres paramètres de modèle. **InterfaceListHelper** s’arrête lorsqu’il n’y a aucun paramètre de modèle restantes.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`TypeT`|Un synonyme du type InterfaceList.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InterfaceListHelper`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)