---
description: 'En savoir plus sur : classe is_trivially_destructible'
title: is_trivially_destructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_destructible
helpviewer_keywords:
- is_trivially_destructible
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
ms.openlocfilehash: 41f36c027175cbf67049eed986b9188ba1532048
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154355"
---
# <a name="is_trivially_destructible-class"></a>is_trivially_destructible, classe

Teste si le type peut être détruit de façon triviale.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_destructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type destructible et que le destructeur est connu du compilateur pour n’utiliser aucune opération non triviale. Sinon, sa valeur est false.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
