---
title: CompareStringOrdinal, méthode
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: c9dbbe8926036ea18210fb30928fafc40093092e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784491"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
La première HSTRING à comparer.

*rhs*<br/>
Le deuxième HSTRING à comparer.

## <a name="return-value"></a>Valeur de retour

|Value|Condition|
|-----------|---------------|
|-1|*LHS* est inférieure à *rhs*.|
|0|*LHS* est égal à *rhs*.|
|1|*LHS* est supérieur à *rhs*.|

## <a name="remarks"></a>Notes

Compare deux objets HSTRING spécifiés et retourne un entier qui indique leur position relative dans un ordre de tri.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::Details, espace de noms](microsoft-wrl-wrappers-details-namespace.md)