---
title: hash, structure (bibliothèque standard C++) | Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: e6d0cea7bfc8cd745e7276f7fc29d493f178fc9b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451948"
---
# <a name="hash-structure-c-standard-library"></a>hash, structure (bibliothèque standard C++)

Définit une fonction membre qui retourne une valeur qui est déterminée de manière unique par `Val`. La fonction membre définit une fonction [hash](../standard-library/hash-class.md) appropriée pour mapper des valeurs de type `thread::id` à une distribution de valeurs d’index.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;

};
```

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> de thread

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<thread>](../standard-library/thread.md)\
[unary_function, struct](../standard-library/unary-function-struct.md)
