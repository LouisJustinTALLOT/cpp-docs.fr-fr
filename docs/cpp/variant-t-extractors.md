---
title: Extracteurs _variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
ms.openlocfilehash: a1b7c713b5d82ff54250b622f2d4afe17abac468
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185604"
---
# <a name="_variant_t-extractors"></a>Extracteurs _variant_t

**Spécifique à Microsoft**

Extrayez les données de l' `VARIANT` objet encapsulé.

## <a name="syntax"></a>Syntaxe

```
operator short( ) const;
operator long( ) const;
operator float( ) const;
operator double( ) const;
operator CY( ) const;
operator _bstr_t( ) const;
operator IDispatch*( ) const;
operator bool( ) const;
operator IUnknown*( ) const;
operator DECIMAL( ) const;
operator BYTE( ) const;
operator VARIANT() const throw();
operator char() const;
operator unsigned short() const;
operator unsigned long() const;
operator int() const;
operator unsigned int() const;
operator __int64() const;
operator unsigned __int64() const;
```

## <a name="remarks"></a>Notes

Extrait des données brutes d’un encapsulé `VARIANT` . Si le `VARIANT` n’est pas déjà le type approprié, `VariantChangeType` est utilisé pour tenter une conversion, et une erreur est générée en cas d’échec :

- **short, opérateur ()** Extrait une **`short`** valeur entière.

- **long, opérateur ()** Extrait une **`long`** valeur entière.

- **float, opérateur ()** Extrait une **`float`** valeur numérique.

- **double (), opérateur** Extrait une **`double`** valeur entière.

- **CY, opérateur ()** Extrait un `CY` objet.

- **operator bool ()** Extrait une **`bool`** valeur.

- **Decimal, opérateur ()** Extrait une `DECIMAL` valeur.

- **Byte (), opérateur** Extrait une `BYTE` valeur.

- **_bstr_t d’opérateur ()** Extrait une chaîne, qui est encapsulée dans un `_bstr_t` objet.

- l' **opérateur IDispatch \* ()** extrait un pointeur dispinterface d’un encapsulé `VARIANT` . `AddRef`est appelé sur le pointeur résultant, c’est pourquoi il vous revient d’appeler `Release` pour le libérer.

- l' **opérateur IUnknown \* ()** extrait un pointeur d’interface com à partir d’un encapsulé `VARIANT` . `AddRef`est appelé sur le pointeur résultant, c’est pourquoi il vous revient d’appeler `Release` pour le libérer.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
