---
title: SafeNotEquals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeNotEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeNotEquals function
ms.assetid: 032e45a8-4159-4b55-b7cc-ecd27f4e4788
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8228a0a269a8f3d726617f2b7adbeb0f016447e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397394"
---
# <a name="safenotequals"></a>SafeNotEquals

Détermine si deux nombres ne sont pas égaux.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Le premier nombre à comparer. Cela doit être de type `T`.

*u*<br/>
[in] Le deuxième nombre à comparer. Cela doit être de type `U`.

## <a name="return-value"></a>Valeur de retour

**true** si *t* et *u* ne sont pas égales ; sinon **false**.

## <a name="remarks"></a>Notes

La méthode améliore `!=` car **SafeNotEquals** vous permet de comparer deux différents types de nombres.

Cette méthode fait partie de [Bibliothèque SafeInt](../windows/safeint-library.md) et est conçu pour une opération de comparaison unique sans créer d’instance de la [classe SafeInt](../windows/safeint-class.md).

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
[SafeEquals](../windows/safeequals.md)