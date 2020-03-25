---
title: _bstr_t::_bstr_t
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
ms.openlocfilehash: 3384da733586c828496a8728a0f5855f92eeec35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190467"
---
# <a name="_bstr_t_bstr_t"></a>_bstr_t::_bstr_t

**Section spécifique de Microsoft**

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

*s2*<br/>
Chaîne multioctet.

*processeur*<br/>
Chaîne Unicode.

*var*<br/>
Objet [_variant_t](../cpp/variant-t-class.md) .

*BSTR*<br/>
Objet `BSTR` existant.

*fCopy*<br/>
Si la valeur est FALSe, l’argument *BSTR* est attaché au nouvel objet sans faire de copie en appelant `SysAllocString`.

## <a name="remarks"></a>Notes

Le tableau ci-dessous décrit les constructeurs `_bstr_t`.

|Constructeur|Description|
|-----------------|-----------------|
|`_bstr_t( )`|Construit un objet `_bstr_t` par défaut qui encapsule un objet `BSTR` null.|
|`_bstr_t( _bstr_t&`  `s1`  `)`|Construit un objet `_bstr_t` comme copie d'un autre.<br /><br /> Il s’agit d’une copie *superficielle* , qui incrémente le décompte de références de l’objet `BSTR` encapsulé au lieu d’en créer un nouveau.|
|`_bstr_t( char*`  `s2`  `)`|Construit un objet `_bstr_t` en appelant `SysAllocString` pour créer un nouvel objet `BSTR`, puis l'encapsule.<br /><br /> Ce constructeur effectue en premier lieu une conversion de chaîne multioctet vers Unicode.|
|`_bstr_t( wchar_t*`  `s3`  `)`|Construit un objet `_bstr_t` en appelant `SysAllocString` pour créer un nouvel objet `BSTR`, puis l'encapsule.|
|`_bstr_t( _variant_t&`  `var`  `)`|Construit un objet `_bstr_t` à partir d'un objet `_variant_t` en extrayant d'abord un objet `BSTR` de l'objet VARIANT encapsulé.|
|`_bstr_t( BSTR``bstr` `, bool``fCopy``)`|Construit un objet `_bstr_t` à partir d’un `BSTR` existant (par opposition à une chaîne `wchar_t*`). Si *fCopy* a la valeur false, le `BSTR` fourni est attaché au nouvel objet sans effectuer de nouvelle copie avec `SysAllocString`.<br /><br /> Ce constructeur est utilisé par les fonctions wrapper dans les en-têtes de bibliothèque de types pour encapsuler et prendre possession d'un `BSTR` retourné par une méthode d'interface.|

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)<br/>
[_variant_t, classe](../cpp/variant-t-class.md)
