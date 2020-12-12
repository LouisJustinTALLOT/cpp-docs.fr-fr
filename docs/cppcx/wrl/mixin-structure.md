---
description: 'En savoir plus sur : structure MixIn'
title: MixIn (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: a438fb6846ae6ba88aaaa968d7b94e8d6636c4aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209384"
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

*Dérivé*<br/>
Un type dérivé de la structure [Implements](implements-structure.md) .

*MixInType*<br/>
Type de base.

*hasImplements*<br/>
**`true`** Si *MixInType* est dérivé de l’implémentation actuelle du type de base ; **`false`** sinon,.

## <a name="remarks"></a>Notes

Si une classe est dérivée de Windows Runtime et d’interfaces COM de classe, la liste des déclarations de classe doit d’abord répertorier toutes les interfaces Windows Runtime, puis toutes les interfaces COM classiques. **MixIn** garantit que les interfaces sont spécifiées dans le bon ordre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`MixIn`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
