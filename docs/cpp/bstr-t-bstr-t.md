---
description: 'En savoir plus sur : _bstr_t :: _bstr_t'
title: _bstr_t::_bstr_t
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
ms.openlocfilehash: efc28b98ecbc6e22c2a78c89e46c08d94e6ce72d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229416"
---
# <a name="_bstr_t_bstr_t"></a>_bstr_t::_bstr_t

**Spécifique à Microsoft**

Construit un objet `_bstr_t`.

## <a name="syntax"></a>Syntaxe

```
_bstr_t( ) throw( );
_bstr_t(
   const _bstr_t& s1
) throw( );
_bstr_t(
   const char* s2
);
_bstr_t(
   const wchar_t* s3
);
_bstr_t(
   const _variant_t& var
);
_bstr_t(
   BSTR bstr,
   bool fCopy
);
```

#### <a name="parameters"></a>Paramètres

*s1*<br/>
Objet `_bstr_t` à copier.

*S2*<br/>
Chaîne multioctet.

*processeur*<br/>
Chaîne Unicode.

*var*<br/>
Objet [_variant_t](../cpp/variant-t-class.md) .

*BSTR*<br/>
Objet `BSTR` existant.

*fCopy*<br/>
Si **`false`** la valeur est, l’argument *BSTR* est attaché au nouvel objet sans faire de copie en appelant `SysAllocString` .

## <a name="remarks"></a>Notes

Le tableau ci-dessous décrit les constructeurs `_bstr_t`.

|Constructeur|Description|
|-----------------|-----------------|
|`_bstr_t( )`|Construit un objet par défaut `_bstr_t` qui encapsule un `BSTR` objet null.|
|`_bstr_t( _bstr_t&`  `s1`  `)`|Construit un objet `_bstr_t` comme copie d'un autre.<br /><br /> Il s’agit d’une copie *superficielle* , qui incrémente le décompte de références de l' `BSTR` objet encapsulé au lieu d’en créer un nouveau.|
|`_bstr_t( char*`  `s2`  `)`|Construit un objet `_bstr_t` en appelant `SysAllocString` pour créer un nouvel objet `BSTR`, puis l'encapsule.<br /><br /> Ce constructeur effectue en premier lieu une conversion de chaîne multioctet vers Unicode.|
|`_bstr_t( wchar_t*`  `s3`  `)`|Construit un objet `_bstr_t` en appelant `SysAllocString` pour créer un nouvel objet `BSTR`, puis l'encapsule.|
|`_bstr_t( _variant_t&`  `var`  `)`|Construit un objet `_bstr_t` à partir d'un objet `_variant_t` en extrayant d'abord un objet `BSTR` de l'objet VARIANT encapsulé.|
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Construit un objet `_bstr_t` à partir d’un `BSTR` existant (par opposition à une chaîne `wchar_t*`). Si *fCopy* a la valeur false, le fourni `BSTR` est attaché au nouvel objet sans effectuer de nouvelle copie avec `SysAllocString` .<br /><br /> Ce constructeur est utilisé par les fonctions wrapper dans les en-têtes de bibliothèque de types pour encapsuler et prendre possession d'un `BSTR` retourné par une méthode d'interface.|

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _bstr_t](../cpp/bstr-t-class.md)<br/>
[Classe _variant_t](../cpp/variant-t-class.md)
