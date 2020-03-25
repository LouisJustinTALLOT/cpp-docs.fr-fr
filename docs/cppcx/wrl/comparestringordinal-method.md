---
title: CompareStringOrdinal, méthode
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: 1291084395b02602b7a3de9013df6720d2e237fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214095"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal, méthode

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
Premier HSTRING à comparer.

*rhs*<br/>
Deuxième HSTRING à comparer.

## <a name="return-value"></a>Valeur de retour

|Valeur|Condition|
|-----------|---------------|
|-1|*LHS* est inférieur à *RHS*.|
|0|*LHS* est égal à *RHS*.|
|1|*LHS* est supérieur à *RHS*.|

## <a name="remarks"></a>Notes

Compare deux objets HSTRING spécifiés et retourne un entier qui indique leur position relative dans un ordre de tri.

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::Details, espace de noms](microsoft-wrl-wrappers-details-namespace.md)
