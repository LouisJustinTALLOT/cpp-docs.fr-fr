---
title: Classe nested_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: ed58eb6cc074b54ae6801d2b11089af9a79f8c8f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441616"
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

Exception stockée capturée par cet objet `nested_exception`.

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Notes

Si `nested_ptr()` retourne un pointeur null, la fonction appelle `std::terminate()`. Dans le cas contraire, il lève l’exception stockée capturée par `*this`.

## <a name="requirements"></a>Spécifications

**En-tête :** \<exception >

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

\ de la [classe d’exception](../standard-library/exception-class.md)
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
