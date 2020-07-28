---
title: _com_ptr_t, extracteurs
description: Décrit les opérateurs d’extraction pour la classe _com_ptr_t.
ms.date: 07/07/2020
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
ms.openlocfilehash: fb5441d87dc35ec6fbb495bc38d9041c1f2d2f33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220572"
---
# <a name="_com_ptr_t-extractors"></a>`_com_ptr_t`Extracteurs

**Spécifique à Microsoft**

Récupérez le pointeur d'interface COM encapsulé.

## <a name="syntax"></a>Syntaxe

```c++
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>Notes

- **`operator Interface*`** Retourne le pointeur d’interface encapsulé, qui peut être NULL.

- **`operator Interface&`** Retourne une référence au pointeur d’interface encapsulé et émet une erreur si le pointeur est NULL.

- **`operator*`** Permet à un objet pointeur intelligent d’agir comme s’il s’agissait de l’interface encapsulée réelle lorsqu’il est déréférencé.

- **`operator->`** Permet à un objet pointeur intelligent d’agir comme s’il s’agissait de l’interface encapsulée réelle lorsqu’il est déréférencé.

- **`operator&`** Libère tout pointeur d’interface encapsulé, en le remplaçant par NULL et retourne l’adresse du pointeur encapsulé. Cet opérateur vous permet de passer le pointeur intelligent par adresse à une fonction qui a un paramètre *out* par le biais duquel elle retourne un pointeur d’interface.

- **`operator bool`** Autorise l’utilisation d’un objet pointeur intelligent dans une expression conditionnelle. Cet opérateur retourne **`true`** si le pointeur n’est pas null.

  > [!NOTE]
  > Étant donné que **`operator bool`** n’est pas déclaré comme **`explicit`** , `_com_ptr_t` est implicitement convertible en **`bool`** , qui peut être converti en un type scalaire. Cela peut avoir des conséquences inattendues dans votre code. Activez l' [Avertissement du compilateur (niveau 4) C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) pour empêcher l’utilisation non intentionnelle de cette conversion.

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)
