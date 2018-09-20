---
title: SafeSubtract | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeSubtract
dev_langs:
- C++
helpviewer_keywords:
- SafeSubtract function
ms.assetid: c2712ddc-173f-46a1-b09c-e7ebbd9e68b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 264a5ccbda8100e7e7fb951a2a8d30e983105efa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375331"
---
# <a name="safesubtract"></a>SafeSubtract

Soustrait deux nombres d’une manière qui protège contre le dépassement de capacité.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Le premier numéro de la soustraction. Cela doit être de type `T`.

*u*<br/>
[in] Le nombre à soustraire de *t*. Cela doit être de type `U`.

*Résultat*<br/>
[out] Le paramètre où **SafeSubtract** stocke le résultat.

## <a name="return-value"></a>Valeur de retour

**true** si aucune erreur ne se produit ; **false** si une erreur se produit.

## <a name="remarks"></a>Notes

Cette méthode fait partie de [Bibliothèque SafeInt](../windows/safeint-library.md) et est conçu pour une opération de soustraction unique sans créer d’instance de la [classe SafeInt](../windows/safeint-class.md).

> [!NOTE]
> Cette méthode doit uniquement être utilisée lorsqu’une opération mathématique unique doit être protégée. S’il existe plusieurs opérations, vous devez utiliser le `SafeInt` classe au lieu d’appeler des fonctions autonomes individuelles.

Pour plus d’informations sur les types de modèle `T` et `U`, consultez [SafeInt, fonctions](../windows/safeint-functions.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** safeint.h

**Namespace :** Microsoft::Utilities

## <a name="see-also"></a>Voir aussi

[SafeInt, fonctions](../windows/safeint-functions.md)<br/>
[Bibliothèque SafeInt](../windows/safeint-library.md)<br/>
[SafeInt, classe](../windows/safeint-class.md)<br/>
[SafeAdd](../windows/safeadd.md)