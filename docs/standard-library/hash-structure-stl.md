---
description: 'En savoir plus sur : structure de hachage (bibliothèque standard C++)'
title: hash, structure (bibliothèque standard C++) | Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: 095566b6855c837c3ee6049a5cbedfbb087420bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324066"
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

## <a name="requirements"></a>Spécifications

**En-tête :**\<thread>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<thread>](../standard-library/thread.md)\
[Struct unary_function](../standard-library/unary-function-struct.md)
