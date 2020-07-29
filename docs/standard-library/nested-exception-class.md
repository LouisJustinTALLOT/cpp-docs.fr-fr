---
title: Classe nested_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 6ae95880f0bc18928ed9bd4f6b6da14722f6ec60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212187"
---
# <a name="nested_exception-class"></a>Classe nested_exception

La classe décrit une exception à utiliser avec l’héritage multiple. Il capture l’exception actuellement gérée et la stocke pour une utilisation ultérieure.

## <a name="syntax"></a>Syntaxe

```cpp
class nested_exception {
    public:
        nested_exception();
        nested_exception(const nested_exception&) = default;
        virtual ~nested_exception() = default; // access functions
};
```

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur =](#op_as)||

### <a name="functions"></a>Fonctions

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|Lève l’exception stockée.|
|[nested_ptr](#nested_ptr)|Retourne l’exception stockée.|

### <a name="operator"></a><a name="op_as"></a>opérateur =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a><a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Valeur de retour

Exception stockée capturée par cet `nested_exception` objet.

### <a name="rethrow_nested"></a><a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Notes

Si `nested_ptr()` retourne un pointeur null, la fonction appelle `std::terminate()` . Dans le cas contraire, il lève l’exception stockée capturée par **`*this`** .

## <a name="requirements"></a>Spécifications

**En-tête :**\<exception>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Classe d’exception](../standard-library/exception-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
