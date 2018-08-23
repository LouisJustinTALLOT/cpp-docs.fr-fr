---
title: SafeAdd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7e84b76f8079656da3ed19aa2c690bf240854015
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594354"
---
# <a name="safeadd"></a>SafeAdd

Ajoute deux nombres d’une manière qui protège contre le dépassement de capacité.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Paramètres

[in] *t*  
Le premier nombre à ajouter. Il doit s’agir de type T.

[in] *u*  
Le deuxième nombre à ajouter. Il doit s’agir de type U.

[out] *résultat*  
Le paramètre où **SafeAdd** stocke le résultat.

## <a name="return-value"></a>Valeur de retour

**true** si aucune erreur ne se produit ; **false** si une erreur se produit.

## <a name="remarks"></a>Notes

Cette méthode fait partie de [Bibliothèque SafeInt](../windows/safeint-library.md) et est conçu pour une opération d’addition unique sans créer d’instance de la [classe SafeInt](../windows/safeint-class.md).

> [!NOTE]
> Cette méthode doit uniquement être utilisée lorsqu’une opération mathématique unique doit être protégée. S’il existe plusieurs opérations, vous devez utiliser le `SafeInt` classe au lieu d’appeler des fonctions autonomes individuelles.

Pour plus d’informations sur les types de modèles T et U, consultez [SafeInt, fonctions](../windows/safeint-functions.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** safeint.h

**Namespace :** Microsoft::Utilities

## <a name="see-also"></a>Voir aussi

[SafeInt, fonctions](../windows/safeint-functions.md)  
[Bibliothèque SafeInt](../windows/safeint-library.md)  
[SafeInt, classe](../windows/safeint-class.md)  
[SafeSubtract](../windows/safesubtract.md)