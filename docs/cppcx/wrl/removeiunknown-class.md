---
title: RemoveIUnknown, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: cfcdefbb8d7cd12d2ebf99710f595fdd2fc16f76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213614"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown, classe

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Une classe.

## <a name="remarks"></a>Notes

Rend un type équivalent à un type basé sur `IUnknown`, mais qui a des fonctions membres `QueryInterface`, `AddRef`et `Release` virtuelles.

Par défaut, les méthodes COM fournissent des méthodes Virtual `QueryInterface`, `AddRef`et `Release`. Toutefois, `ComPtr` ne nécessite pas la surcharge des méthodes virtuelles. `RemoveIUnknown` élimine cette surcharge en fournissant des méthodes privées, invirtuelles `QueryInterface`, `AddRef`et `Release`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`ReturnType`|Synonyme pour un type qui est équivalent au paramètre de modèle *T* mais qui a des membres de `IUnknown` non virtuels.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)
