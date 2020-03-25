---
title: MixIn (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: b302d6e08e401a24b465508d5ddabcae8b16bd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213692"
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

*Issue*<br/>
Un type dérivé de la structure [Implements](implements-structure.md) .

*MixInType*<br/>
Type de base.

*hasImplements*<br/>
**true** si *MixInType* est dérivé de l’implémentation actuelle du type de base ; **false** dans le cas contraire.

## <a name="remarks"></a>Notes

Si une classe est dérivée de Windows Runtime et d’interfaces COM de classe, la liste des déclarations de classe doit d’abord répertorier toutes les interfaces Windows Runtime, puis toutes les interfaces COM classiques. **MixIn** garantit que les interfaces sont spécifiées dans le bon ordre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`MixIn`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)
