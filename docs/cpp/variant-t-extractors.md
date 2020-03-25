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
ms.openlocfilehash: 685df7285e58e0cf2ceeded5ac27641364897298
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187698"
---
# <a name="_variant_t-extractors"></a>Extracteurs _variant_t

**Section spécifique de Microsoft**

Extrayez les données de l’objet `VARIANT` encapsulé.

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

Extrait des données brutes d’un `VARIANT`encapsulé. Si le `VARIANT` n’est pas déjà du type approprié, `VariantChangeType` est utilisé pour tenter une conversion, et une erreur est générée en cas d’échec :

- **short, opérateur ()** Extrait une valeur entière de type **short** .

- **long, opérateur ()** Extrait une valeur entière de **type long** .

- **float, opérateur ()** Extrait une valeur numérique à **virgule flottante** .

- **double (), opérateur** Extrait une valeur d’entier **double** .

- **CY, opérateur ()** Extrait un objet `CY`.

- **operator bool ()** Extrait une valeur **bool** .

- **Decimal, opérateur ()** Extrait une valeur `DECIMAL`.

- **Byte (), opérateur** Extrait une valeur `BYTE`.

- **_bstr_t d’opérateur ()** Extrait une chaîne, qui est encapsulée dans un objet `_bstr_t`.

- **\*IDispatch, opérateur ()** Extrait un pointeur dispinterface d’un `VARIANT`encapsulé. `AddRef` est appelé sur le pointeur résultant, il vous revient d’appeler `Release` pour le libérer.

- **\*IUnknown, opérateur ()** Extrait un pointeur d’interface COM à partir d’un `VARIANT`encapsulé. `AddRef` est appelé sur le pointeur résultant, il vous revient d’appeler `Release` pour le libérer.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)
