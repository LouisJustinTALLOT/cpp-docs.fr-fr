---
description: 'En savoir plus sur : classe Removeiunknown,'
title: RemoveIUnknown, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: 0ef00ee9859a27252550aaeec6fb9b4f9ef2d5b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278725"
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

Rend un type équivalent à un `IUnknown` type basé sur, mais avec des `QueryInterface` `AddRef` fonctions membres, et non virtuelles `Release` .

Par défaut, les méthodes COM fournissent des méthodes virtuelles `QueryInterface` , `AddRef` et `Release` . Toutefois, `ComPtr` ne nécessite pas la surcharge des méthodes virtuelles. `RemoveIUnknown` élimine cette surcharge en fournissant des méthodes privées, invirtuelles, `QueryInterface` `AddRef` et `Release` .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`ReturnType`|Synonyme pour un type qui est équivalent au paramètre de modèle *T* mais qui a des `IUnknown` membres non virtuels.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL ::D espace de noms étails](microsoft-wrl-details-namespace.md)
