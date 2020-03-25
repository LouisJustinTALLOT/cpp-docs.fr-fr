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
ms.openlocfilehash: 31ac39104c041d1d119f6cd06de5f9c4a620dac0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190025"
---
# <a name="_com_ptr_t-extractors"></a>_com_ptr_t, extracteurs

**Section spécifique de Microsoft**

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

- l' **interface d’opérateur** <strong>\*</strong> retourne le pointeur d’interface encapsulé, qui peut être null.

- **&** de l’interface d’opérateur Retourne une référence au pointeur d’interface encapsulé et émet une erreur si le pointeur est NULL.

- l' **opérateur** <strong>\*</strong> permet à un objet pointeur intelligent d’agir comme s’il s’agissait de l’interface encapsulée réelle lorsqu’il est déréférencé.

- **> Operator** Permet à un objet pointeur intelligent d’agir comme s’il s’agissait de l’interface encapsulée réelle lorsqu’il est déréférencé.

- **& d’opérateur** Libère tout pointeur d’interface encapsulé, en le remplaçant par NULL et retourne l’adresse du pointeur encapsulé. Cela permet de passer le pointeur intelligent par adresse à une fonction qui a un paramètre *out* par le biais duquel elle retourne un pointeur d’interface.

- **bool, opérateur** Autorise l’utilisation d’un objet pointeur intelligent dans une expression conditionnelle. Cet opérateur retourne la valeur TRUE si le pointeur n’a pas la valeur NULL.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)
