---
title: Removeiunknown, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs:
- C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11751bf4e6f43e18fddb71a5ba2fd331a6d36977
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599369"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown, classe

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T
>
struct RemoveIUnknown;

template <
   typename T
>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Paramètres

*T*  
Une classe.

## <a name="remarks"></a>Notes

Crée un type qui est équivalent à une `IUnknown`-en fonction de type, mais a non virtuelle `QueryInterface`, `AddRef`, et `Release` fonctions membres.

Par défaut, les méthodes COM fournissent virtuel `QueryInterface`, `AddRef`, et `Release` méthodes. Toutefois, `ComPtr` ne nécessite pas la surcharge de méthodes virtuelles. `RemoveIUnknown` élimine cette surcharge en fournissant privé et non virtuelle `QueryInterface`, `AddRef`, et `Release` méthodes.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`ReturnType`|Un synonyme pour un type qui est équivalent au paramètre de modèle *T* mais a non virtuelle `IUnknown` membres.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)