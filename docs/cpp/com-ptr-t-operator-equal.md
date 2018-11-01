---
title: _com_ptr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.operator=
- _com_ptr_t::operator=
helpviewer_keywords:
- operator = [C++], pointers
- = operator [C++], with specific Visual C++ objects
- operator= [C++], pointers
ms.assetid: 46849455-371c-4d0f-bae4-c1f737d2ca4a
ms.openlocfilehash: 16125576ddd72e66a1ed64486f1668f268de9cb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530206"
---
# <a name="comptrtoperator-"></a>_com_ptr_t::operator =

**Section spécifique à Microsoft**

Assigne une nouvelle valeur à un objet `_com_ptr_t` existant.

## <a name="syntax"></a>Syntaxe

```
template<typename _OtherIID> 
_com_ptr_t& operator=( const _com_ptr_t<_OtherIID>& p );

// Sets a smart pointer to be a different smart pointer of a different
// type or a different raw interface pointer. QueryInterface is called
// to find an interface pointer of this smart pointer's type, and
// Release is called to decrement the reference count for the previously
// encapsulated pointer. If QueryInterface fails with an E_NOINTERFACE,
// a NULL smart pointer results.
template<typename _InterfaceType> 
_com_ptr_t& operator=(_InterfaceType* p );

// Encapsulates a raw interface pointer of this smart pointer's type.
// AddRef is called to increment the reference count for the encapsulated
// interface pointer, and Release is called to decrement the reference
// count for the previously encapsulated pointer.
template<> _com_ptr_t&  
operator=( Interface* pInterface ) throw();

// Sets a smart pointer to be a copy of another instance of the same
// smart pointer of the same type. AddRef is called to increment the
// reference count for the encapsulated interface pointer, and Release
// is called to decrement the reference count for the previously
// encapsulated pointer.
_com_ptr_t& operator=( const _com_ptr_t& cp ) throw();

// Sets a smart pointer to NULL. The NULL argument must be a zero.
_com_ptr_t& operator=( int null );

// Sets a smart pointer to be a _variant_t object. The encapsulated
// VARIANT must be of type VT_DISPATCH or VT_UNKNOWN, or it can be
// converted to one of these two types. If QueryInterface fails with an
// E_NOINTERFACE error, a NULL smart pointer results.
_com_ptr_t& operator=( const _variant_t& varSrc );
```

## <a name="remarks"></a>Notes

Assigne un pointeur d'interface vers cet objet `_com_ptr_t`.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)