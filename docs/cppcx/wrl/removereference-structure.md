---
title: RemoveReference (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RemoveReference
helpviewer_keywords:
- RemoveReference structure
ms.assetid: 43ff91bb-815a-440e-b9fb-7dcbb7c863af
ms.openlocfilehash: 7753c1ad41f12fa8c14d2f10c9e2f91e043a5846
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213601"
---
# <a name="removereference-structure"></a>RemoveReference (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
struct RemoveReference;

template<class T>
struct RemoveReference<T&>;

template<class T>
struct RemoveReference<T&&>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Une classe.

## <a name="remarks"></a>Notes

Supprime la référence ou la caractéristique de référence rvalue du paramètre de modèle de classe spécifié.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`Type`|Synonyme du paramètre de modèle de classe.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`RemoveReference`

## <a name="requirements"></a>Spécifications

**En-tête :** Internal. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)
