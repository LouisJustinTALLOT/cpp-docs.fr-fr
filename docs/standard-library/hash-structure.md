---
title: hash, structure
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::hash
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
ms.openlocfilehash: b8484c8987534051c79ea02a1f87f0df1cd1f027
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456363"
---
# <a name="hash-structure"></a>hash, structure

La classe de modèle définit sa méthode comme retournant `val.hash_code()`. La méthode définit une fonction de hachage qui sert à mapper les valeurs de type [type_index](../standard-library/type-index-class.md) à une distribution de valeurs d’index.

## <a name="syntax"></a>Syntaxe

```cpp
template <> struct hash<type_index>
: public unary_function<type_index, size_t>
{ // hashes a typeinfo object
    size_t operator()(type_index val) const;
};
```

## <a name="specialized-types"></a>Types spécialisés

### <a name="system_error"></a>\<system_error >

```cpp
template <class T> struct hash;
template <> struct hash<error_code>;
template <> struct hash<error_condition>;
```

## <a name="see-also"></a>Voir aussi

[\<typeindex>](../standard-library/typeindex.md)
