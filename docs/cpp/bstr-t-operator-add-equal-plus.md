---
description: 'En savoir plus sur : _bstr_t :: Operator + =, +'
title: _bstr_t::operator +=, +
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
ms.openlocfilehash: e3ae71a3a43e189251ac0ddaf77572656a031aaf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308807"
---
# <a name="_bstr_toperator--"></a>_bstr_t::operator +=, +

**Spécifique à Microsoft**

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
Objet `_bstr_t`.

*S2*<br/>
Chaîne multioctet.

*processeur*<br/>
Chaîne Unicode.

## <a name="remarks"></a>Notes

Ces opérateurs exécutent une concaténation de chaînes :

- **opérateur + = (**  *S1*  **)** Ajoute les caractères dans le encapsulé `BSTR` de *S1* à la fin de l’encapsulation de cet objet `BSTR` .

- **opérateur + (**  *S1*  **)** Retourne le nouveau `_bstr_t` formé en concaténant cet objet `BSTR` avec celui de *S1*.

- **opérateur + (***S2* **&#124;** *S1***)** Retourne un nouveau `_bstr_t` formé en concaténant une chaîne multioctets *S2*, convertie en Unicode, avec le `BSTR` encapsulé dans *S1*.        

- **opérateur + (**  *S3* **,**  *S1*  **)** Retourne un nouveau `_bstr_t` formé en concaténant une chaîne Unicode *S3* avec le `BSTR` encapsulé dans *S1*.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _bstr_t](../cpp/bstr-t-class.md)
