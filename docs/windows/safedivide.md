---
title: SafeDivide | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeDivide
dev_langs:
- C++
helpviewer_keywords:
- SafeDivide function
ms.assetid: b5b27484-ad6e-46b1-ba9f-1c7120dd103b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98f37a428c81276788ea4aef315e7266a9da02c4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383400"
---
# <a name="safedivide"></a>SafeDivide

Divise deux nombres d’une manière qui protège contre la division par zéro.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Le diviseur. Il doit s’agir de type T.

*u*<br/>
[in] Le dividende. Il doit s’agir de type U.

*Résultat*<br/>
[out] Le paramètre où **SafeDivide** stocke le résultat.

## <a name="return-value"></a>Valeur de retour

**true** si aucune erreur ne se produit ; **false** si une erreur se produit.

## <a name="remarks"></a>Notes

Cette méthode fait partie de [Bibliothèque SafeInt](../windows/safeint-library.md) et est conçu pour une opération de division unique sans créer d’instance de la [classe SafeInt](../windows/safeint-class.md).

> [!NOTE]
> Cette méthode doit uniquement être utilisée lorsqu’une opération mathématique unique doit être protégée. S’il existe plusieurs opérations, vous devez utiliser le `SafeInt` classe au lieu d’appeler des fonctions autonomes individuelles.

Pour plus d’informations sur les types de modèles T et U, consultez [SafeInt, fonctions](../windows/safeint-functions.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** safeint.h

**Namespace :** Microsoft::Utilities

## <a name="see-also"></a>Voir aussi

[SafeInt, fonctions](../windows/safeint-functions.md)<br/>
[Bibliothèque SafeInt](../windows/safeint-library.md)<br/>
[SafeInt, classe](../windows/safeint-class.md)<br/>
[SafeModulus](../windows/safemodulus.md)<br/>
[SafeMultiply](../windows/safemultiply.md)