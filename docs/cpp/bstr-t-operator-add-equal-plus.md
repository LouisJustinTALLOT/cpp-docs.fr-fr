---
title: _bstr_t::operator +=, +
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
ms.openlocfilehash: b9eddca85d66f4978e1b33299ca655cd880cf45e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181146"
---
# <a name="_bstr_toperator--"></a>_bstr_t::operator +=, +

**Section spécifique de Microsoft**

Ajoute des caractères à la fin de l'objet `_bstr_t` ou concatène deux chaînes.

## <a name="syntax"></a>Syntaxe

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>Paramètres

*s1*<br/>
Objet `_bstr_t` .

*s2*<br/>
Chaîne multioctet.

*processeur*<br/>
Chaîne Unicode.

## <a name="remarks"></a>Notes

Ces opérateurs exécutent une concaténation de chaînes :

- **opérateur + = (**  *S1*  **)** Ajoute les caractères de l' `BSTR` encapsulé de *S1* à la fin du `BSTR`encapsulé de cet objet.

- **opérateur + (**  *S1*  **)** Retourne le nouvel `_bstr_t` formé en concaténant le `BSTR` de cet objet avec celui de *S1*.

- **opérateur + (**  *S2*  **&#124;**  *S1*  **)** Retourne une nouvelle `_bstr_t` formée par la concaténation d’une chaîne multioctets *S2*, convertie en Unicode, avec l' `BSTR` encapsulé dans *S1*.

- **opérateur + (**  *S3* **,**  *S1*  **)** Retourne une nouvelle `_bstr_t` formée par la concaténation d’une chaîne Unicode *S3* avec l' `BSTR` encapsulé dans *S1*.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)
