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
ms.openlocfilehash: 6a8f31e8db6f5ca5a680dd47b5d5391c84ce5025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403312"
---
# <a name="varianttoperator-"></a>_variant_t::operator =

**Section spécifique à Microsoft**

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

- **opérateur = (***varSrc***)** attribue un existant `VARIANT` à un `_variant_t` objet.

- **opérateur = (***pVarSrc***)** attribue un existant `VARIANT` à un `_variant_t` objet.

- **opérateur = (***var_t_Src***)** attribue un existant `_variant_t` de l’objet à un `_variant_t` objet.    

- **opérateur = (***sSrc***)** attribue un **court** valeur entière à un `_variant_t` objet.

- **opérateur = (**`lSrc`**)** attribue un **long** valeur entière à un `_variant_t` objet.

- **opérateur = (***fltSrc***)** attribue un **float** valeur numérique à un `_variant_t` objet.

- **operator=(**  *dblSrc*  **)** Assigns a **double** numerical value to a `_variant_t` object.

- **opérateur = (***cySrc***)** attribue un `CY` de l’objet à un `_variant_t` objet.

- **opérateur = (***bstrSrc***)** attribue un `BSTR` de l’objet à un `_variant_t` objet.

- **opérateur = (***wstrSrc***)** assigne une chaîne Unicode à un `_variant_t` objet.

- **opérateur = (**`strSrc`**)** assigne une chaîne multioctet à un `_variant_t` objet.

- **opérateur = (** `bSrc` **)** attribue un **bool** valeur un `_variant_t` objet.

- **opérateur = (***pDispSrc***)** attribue un `VT_DISPATCH` de l’objet à un `_variant_t` objet.

- **opérateur = (***pIUnknownSrc***)** attribue un `VT_UNKNOWN` de l’objet à un `_variant_t` objet.

- **opérateur = (***decSrc***)** attribue un `DECIMAL` valeur un `_variant_t` objet.

- **opérateur = (** `bSrc` **)** attribue un `BYTE` valeur un `_variant_t` objet.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)