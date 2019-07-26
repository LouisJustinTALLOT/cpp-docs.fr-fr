---
title: nested_exception, classe
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 5741b3aa255f915500f5fe79ab5374c8c86f8814
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460180"
---
# <a name="nestedexception-class"></a>nested_exception, classe

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
|[operator=](#op_as)||

### <a name="functions"></a>Fonctions

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|Lève l’exception stockée.|
|[nested_ptr](#nested_ptr)|Retourne l’exception stockée.|

### <a name="op_as"></a>opérateur =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Valeur de retour

Exception stockée capturée par `nested_exception` cet objet.

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Notes

Si `nested_ptr()` retourne un pointeur null, la fonction appelle `std::terminate()`. Dans le cas contraire, il lève l’exception stockée capturée par `*this`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<exception>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Classe d’exception](../standard-library/exception-class.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
