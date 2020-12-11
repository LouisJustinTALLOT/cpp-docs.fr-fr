---
description: 'En savoir plus sur : _variant_t :: Operator ='
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: a304f0904f697ade7d04c6d12f375571a156e989
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161466"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

**Spécifique à Microsoft**

## <a name="syntax"></a>Syntaxe

```
_variant_t& operator=(
   const VARIANT& varSrc
);

_variant_t& operator=(
   const VARIANT* pVarSrc
);

_variant_t& operator=(
   const _variant_t& var_t_Src
);

_variant_t& operator=(
   short sSrc
);

_variant_t& operator=(
   long lSrc
);

_variant_t& operator=(
   float fltSrc
);

_variant_t& operator=(
   double dblSrc
);

_variant_t& operator=(
   const CY& cySrc
);

_variant_t& operator=(
   const _bstr_t& bstrSrc
);

_variant_t& operator=(
   const wchar_t* wstrSrc
);

_variant_t& operator=(
   const char* strSrc
);

_variant_t& operator=(
   IDispatch* pDispSrc
);

_variant_t& operator=(
   bool bSrc
);

_variant_t& operator=(
   IUnknown* pSrc
);

_variant_t& operator=(
   const DECIMAL& decSrc
);

_variant_t& operator=(
   BYTE bSrc
);

_variant_t& operator=(
   char cSrc
);

_variant_t& operator=(
   unsigned short usSrc
);

_variant_t& operator=(
   unsigned long ulSrc
);

_variant_t& operator=(
   int iSrc
);

_variant_t& operator=(
   unsigned int uiSrc
);

_variant_t& operator=(
   __int64 i8Src
);

_variant_t& operator=(
   unsigned __int64 ui8Src
);
```

## <a name="remarks"></a>Notes

L'opérateur assigne une nouvelle valeur à l'objet `_variant_t` :

- **opérateur = (**  *varSrc*  **)** Assigne un existant `VARIANT` à un `_variant_t` objet.

- **opérateur = (**  *pVarSrc*  **)** Assigne un existant `VARIANT` à un `_variant_t` objet.

- **opérateur = (**  *var_t_Src*  **)** Assigne un `_variant_t` objet existant à un `_variant_t` objet.

- **opérateur = (**  *sSrc*  **)** Assigne une **`short`** valeur entière à un `_variant_t` objet.

- **Operator = (** `lSrc` **)** assigne une **`long`** valeur entière à un `_variant_t` objet.    

- **opérateur = (**  *fltSrc*  **)** Assigne une **`float`** valeur numérique à un `_variant_t` objet.

- **opérateur = (**  *dblSrc*  **)** Assigne une **`double`** valeur numérique à un `_variant_t` objet.

- **opérateur = (**  *cySrc*  **)** Assigne un `CY` objet à un `_variant_t` objet.

- **opérateur = (**  *bstrSrc*  **)** Assigne un `BSTR` objet à un `_variant_t` objet.

- **opérateur = (**  *wstrSrc*  **)** Assigne une chaîne Unicode à un `_variant_t` objet.

- **Operator = (** `strSrc` **)** assigne une chaîne multioctets à un `_variant_t` objet.    

- **Operator = (** `bSrc` **)** assigne une **`bool`** valeur à un `_variant_t` objet.  

- **opérateur = (**  *pDispSrc*  **)** Assigne un `VT_DISPATCH` objet à un `_variant_t` objet.

- **opérateur = (**  *pIUnknownSrc*  **)** Assigne un `VT_UNKNOWN` objet à un `_variant_t` objet.

- **opérateur = (**  *decSrc*  **)** Assigne une `DECIMAL` valeur à un `_variant_t` objet.

- **Operator = (** `bSrc` **)** assigne une `BYTE` valeur à un `_variant_t` objet.  

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
