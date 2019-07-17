---
title: nested_exception, classe
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: a568a8d9a3817883656406d63c3dd948539bb385
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268521"
---
# <a name="nestedexception-class"></a>nested_exception, classe

La classe décrit une exception pour une utilisation avec l’héritage multiple. Il capture l’exception actuellement gérée et le stocke pour une utilisation ultérieure.

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

### <a name="op_as"></a> opérateur =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a> nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Valeur de retour

L’exception stockée capturé par ce `nested_exception` objet.

### <a name="rethrow_nested"></a> rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Notes

Si `nested_ptr()` retourne un pointeur null, la fonction appelle `std::terminate()`. Sinon, il lève l’exception stockée capturée par `*this`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<exception>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[exception, classe](../standard-library/exception-class.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
