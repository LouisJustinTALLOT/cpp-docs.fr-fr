---
title: SafeEquals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeEquals function
ms.assetid: 6019627d-f170-413b-9abd-2b5b34396a72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81f30386946c7fd187f1044804b9f1737a94c58f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718644"
---
# <a name="safeequals"></a>SafeEquals

Compare deux nombres pour déterminer s’ils sont égaux.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Le premier nombre à comparer. Il doit s’agir de type T.

*u*<br/>
[in] Le deuxième nombre à comparer. Il doit s’agir de type U.

## <a name="return-value"></a>Valeur de retour

**true** si *t* et *u* sont égales ; sinon **false**.

## <a name="remarks"></a>Notes

La méthode améliore `==` car **SafeEquals** vous permet de comparer deux différents types de nombres.

Cette méthode fait partie de [Bibliothèque SafeInt](../windows/safeint-library.md) et est conçu pour une opération de comparaison unique sans créer d’instance de la [classe SafeInt](../windows/safeint-class.md).

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
[SafeNotEquals](../windows/safenotequals.md)