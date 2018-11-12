---
title: _com_ptr_t, extracteurs
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
ms.openlocfilehash: 494507592222a7cd6334f2272c3a306e61e5d47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545975"
---
# <a name="comptrt-extractors"></a>_com_ptr_t, extracteurs

**Section spécifique à Microsoft**

Récupérez le pointeur d'interface COM encapsulé.

## <a name="syntax"></a>Syntaxe

```
operator Interface*( ) const throw( ); 
operator Interface&( ) const; 
Interface& operator*( ) const; 
Interface* operator->( ) const; 
Interface** operator&( ) throw( ); 
operator bool( ) const throw( );
```

## <a name="remarks"></a>Notes

- **operator Interface** <strong>\*</strong> retourne le pointeur d’interface encapsulé, ce qui peut être NULL.

- **operator Interface &** retourne une référence au pointeur d’interface encapsulé et émet une erreur si le pointeur est NULL.

- **opérateur** <strong>\*</strong> permet à un objet pointeur intelligent d’agir comme s’il s’agissait de l’interface encapsulée réelle fois déréférencé.

- **operator ->** permet à un objet pointeur intelligent d’agir comme s’il s’agissait de l’interface encapsulée réelle fois déréférencé.

- **opérateur &** libère tout pointeur d’interface encapsulé, en la remplaçant par une valeur NULL et retourne l’adresse du pointeur encapsulé. Ainsi, le pointeur intelligent à passer par adresse à une fonction qui a un *out* paramètre par le biais duquel elle retourne un pointeur d’interface.

- **opérateur bool** permet à un objet pointeur intelligent à utiliser dans une expression conditionnelle. Cet opérateur retourne TRUE si le pointeur n’est pas NULL.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)