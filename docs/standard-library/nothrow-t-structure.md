---
title: nothrow_t, structure
ms.date: 11/04/2016
f1_keywords:
- nothrow_t
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
ms.openlocfilehash: 2313c436a1fd25149fa7ea72f122a6f323b40028
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575797"
---
# <a name="nothrowt-structure"></a>nothrow_t, structure

Le struct est utilisé comme paramètre de fonction de l’opérateur new pour indiquer que la fonction doit retourner un pointeur null pour signaler un échec d’allocation, au lieu de lever une exception.

## <a name="syntax"></a>Syntaxe

```cpp
struct std::nothrow_t {};
```

## <a name="remarks"></a>Notes

Le struct aide le compilateur à sélectionner la version correcte du constructeur. [nothrow](../standard-library/new-functions.md#nothrow) est un synonyme des objets de type `std::nothrow_t`.

## <a name="example"></a>Exemple

Pour obtenir des exemples d’utilisation de `std::nothrow_t` comme paramètre de fonction, consultez [new, opérateur](../standard-library/new-operators.md#op_new) et [new &#91;&#93;, opérateur](../standard-library/new-operators.md#op_new_arr).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<new>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
