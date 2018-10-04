---
title: MixIn, Structure | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e4a9e9eb2804e5abbb3f84ab157043402d48166f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789096"
---
# <a name="mixin-structure"></a>MixIn (structure)

Garantit qu'une classe d'exécution dérive des interfaces du Windows Runtime, le cas échéant, puis des interfaces du COM classique.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>Paramètres

*DÉRIVÉS*<br/>
Un type dérivé le [implémente](../windows/implements-structure.md) structure.

*MixInType*<br/>
Type de base.

*hasImplements*<br/>
**true** si *MixInType* est dérivée de l’implémentation actuelle du type de base ; **false** dans le cas contraire.

## <a name="remarks"></a>Notes

Si une classe est dérivée de Windows Runtime et des interfaces de classes COM, puis un COM classique interfaces et la liste de déclaration de classe doit tout d’abord répertoriez toutes les interfaces Windows Runtime. **MixIn** garantit que les interfaces sont spécifiées dans l’ordre approprié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`MixIn`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)