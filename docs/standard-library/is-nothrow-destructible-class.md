---
description: 'En savoir plus sur : classe is_nothrow_destructible'
title: is_nothrow_destructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_destructible
helpviewer_keywords:
- is_nothrow_destructible
ms.assetid: 0bbd8a28-e312-4d72-bd28-aac027f974d3
ms.openlocfilehash: 017cc6de7ce5c618fcc3f47540efd34b5fdc40a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323616"
---
# <a name="is_nothrow_destructible-class"></a>is_nothrow_destructible, classe

Teste si le type est destructible et si le destructeur est connu du compilateur comme ne levant pas d’exception.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_nothrow_destructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type destructible et que le destructeur est connu du fait que le compilateur ne lève pas d’exception. Sinon, sa valeur est false.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
