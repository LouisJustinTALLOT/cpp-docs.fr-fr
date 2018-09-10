---
title: is_trivially_copyable, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copyable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1577f067b398a53ab4f91847f890beaa96f0639f
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102809"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable, classe

Teste si le type peut être copié de façon triviale.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type COPIABLE, sinon, sa valeur est false. Les types qui peuvent être copiés de façon triviale ont des opérations de copie, des opérations de déplacement ou des destructeurs non triviaux. En règle générale, une opération de copie est considérée comme triviale si elle peut être implémentée comme copie au niveau du bit. Les types intégrés et les tableaux de types pouvant être copiés de manière triviale peuvent être copiés de manière triviale.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
