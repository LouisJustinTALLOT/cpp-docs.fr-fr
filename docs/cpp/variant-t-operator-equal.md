---
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: 402251592a87b723d75fd1b2cd0786be7b17dbfc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187620"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

**Section spécifique de Microsoft**

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

- **opérateur = (**  *varSrc*  **)** Affecte un `VARIANT` existant à un objet `_variant_t`.

- **opérateur = (**  *pVarSrc*  **)** Affecte un `VARIANT` existant à un objet `_variant_t`.

- **opérateur = (**  *var_t_Src*  **)** Assigne un objet `_variant_t` existant à un objet `_variant_t`.

- **opérateur = (**  *sSrc*  **)** Assigne une valeur entière **short** à un objet `_variant_t`.

- **opérateur = (** `lSrc` **)** Assigne une valeur entière **longue** à un objet `_variant_t`.

- **opérateur = (**  *fltSrc*  **)** Assigne une valeur numérique à **virgule flottante** à un objet `_variant_t`.

- **opérateur = (**  *dblSrc*  **)** Assigne une valeur numérique **double** à un objet `_variant_t`.

- **opérateur = (**  *cySrc*  **)** Assigne un objet `CY` à un objet `_variant_t`.

- **opérateur = (**  *bstrSrc*  **)** Assigne un objet `BSTR` à un objet `_variant_t`.

- **opérateur = (**  *wstrSrc*  **)** Assigne une chaîne Unicode à un objet `_variant_t`.

- **opérateur = (** `strSrc` **)** Assigne une chaîne multioctets à un objet `_variant_t`.

- **opérateur = (** `bSrc` **)** Assigne une valeur **bool** à un objet `_variant_t`.

- **opérateur = (**  *pDispSrc*  **)** Assigne un objet `VT_DISPATCH` à un objet `_variant_t`.

- **opérateur = (**  *pIUnknownSrc*  **)** Assigne un objet `VT_UNKNOWN` à un objet `_variant_t`.

- **opérateur = (**  *decSrc*  **)** Assigne une valeur `DECIMAL` à un objet `_variant_t`.

- **opérateur = (** `bSrc` **)** Assigne une valeur `BYTE` à un objet `_variant_t`.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)
