---
title: is_trivially_destructible, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_destructible
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89215ac3d7b1035ef4326d73b21d540aada5fba6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857813"
---
# <a name="istriviallydestructible-class"></a>is_trivially_destructible, classe

Teste si le type peut être détruit de façon triviale.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_destructible;
```

### <a name="parameters"></a>Paramètres

`T` Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type `T` est un type destructible et que le destructeur est connu du compilateur comme n’utilisant aucune opération non triviale. Sinon, sa valeur est false.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
