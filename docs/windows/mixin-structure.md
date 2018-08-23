---
title: MixIn, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6ccea9a053f47ae206cbe5c8412c387f07bd5b52
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603425"
---
# <a name="mixin-structure"></a>MixIn (structure)

Garantit qu'une classe d'exécution dérive des interfaces du Windows Runtime, le cas échéant, puis des interfaces du COM classique.

## <a name="syntax"></a>Syntaxe

```cpp
template<
   typename Derived,
   typename MixInType,
   bool hasImplements = __is_base_of(Details::ImplementsBase,
   MixInType)  
>
struct MixIn;
```

### <a name="parameters"></a>Paramètres

*DÉRIVÉS*  
Un type dérivé le [implémente](../windows/implements-structure.md) structure.

*MixInType*  
Type de base.

*hasImplements*  
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