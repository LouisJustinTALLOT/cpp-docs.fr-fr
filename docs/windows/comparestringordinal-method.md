---
title: Comparestringordinal, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs:
- C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9fba5ff2db133d7a510499bd79de8bb77119eb79
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387209"
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

*LHS*<br/>
La première HSTRING à comparer.

*terme de droite*<br/>
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

**Namespace :** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::Details, espace de noms](../windows/microsoft-wrl-wrappers-details-namespace.md)