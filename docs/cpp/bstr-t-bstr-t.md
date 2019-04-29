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
ms.openlocfilehash: 44a301b8b2a1c53636c27be6f59f61aa0dcd46b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385009"
---
# <a name="bstrtbstrt"></a>_bstr_t::_bstr_t

**Section spécifique à Microsoft**

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

*s3*<br/>
Chaîne Unicode.

*var*<br/>
Un [_variant_t](../cpp/variant-t-class.md) objet.

*bstr*<br/>
Objet `BSTR` existant.

*fCopy*<br/>
Si la valeur est FALSE, le *bstr* argument est attaché au nouvel objet sans avoir à effectuer une copie en appelant `SysAllocString`.

## <a name="remarks"></a>Notes

Le tableau ci-dessous décrit les constructeurs `_bstr_t`.

|Constructeur|Description|
|-----------------|-----------------|
|`_bstr_t( )`|Construit une valeur par défaut `_bstr_t` objet qui encapsule une valeur null `BSTR` objet.|
|`_bstr_t( _bstr_t&`  `s1`  `)`|Construit un objet `_bstr_t` comme copie d'un autre.<br /><br /> Il s’agit d’un *superficielle* copie, ce qui incrémente le décompte de références d’encapsulé `BSTR` objet au lieu de créer un nouveau.|
|`_bstr_t( char*`  `s2`  `)`|Construit un objet `_bstr_t` en appelant `SysAllocString` pour créer un nouvel objet `BSTR`, puis l'encapsule.<br /><br /> Ce constructeur effectue en premier lieu une conversion de chaîne multioctet vers Unicode.|
|`_bstr_t( wchar_t*`  `s3`  `)`|Construit un objet `_bstr_t` en appelant `SysAllocString` pour créer un nouvel objet `BSTR`, puis l'encapsule.|
|`_bstr_t( _variant_t&`  `var`  `)`|Construit un objet `_bstr_t` à partir d'un objet `_variant_t` en extrayant d'abord un objet `BSTR` de l'objet VARIANT encapsulé.|
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Construit un objet `_bstr_t` à partir d’un `BSTR` existant (par opposition à une chaîne `wchar_t*`). Si *fCopy* a la valeur false, le texte fourni `BSTR` est attaché au nouvel objet sans avoir à effectuer une nouvelle copie avec `SysAllocString`.<br /><br /> Ce constructeur est utilisé par les fonctions wrapper dans les en-têtes de bibliothèque de types pour encapsuler et prendre possession d'un `BSTR` retourné par une méthode d'interface.|

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)<br/>
[_variant_t, classe](../cpp/variant-t-class.md)