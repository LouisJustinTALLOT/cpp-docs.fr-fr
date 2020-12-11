---
description: 'En savoir plus sur : _variant_t :: _variant_t'
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: e49f2cf42ce1d73cb18d280d335ed267cb11df3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161362"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Spécifique à Microsoft**

Construit un objet `_variant_t`.

## <a name="syntax"></a>Syntaxe

```
_variant_t( ) throw( );

_variant_t(
   const VARIANT& varSrc
);

_variant_t(
   const VARIANT* pVarSrc
);

_variant_t(
   const _variant_t& var_t_Src
);

_variant_t(
   VARIANT& varSrc,
   bool fCopy
);

_variant_t(
   short sSrc,
   VARTYPE vtSrc = VT_I2
);

_variant_t(
   long lSrc,
   VARTYPE vtSrc = VT_I4
);

_variant_t(
   float fltSrc
) throw( );

_variant_t(
   double dblSrc,
   VARTYPE vtSrc = VT_R8
);

_variant_t(
   const CY& cySrc
) throw( );

_variant_t(
   const _bstr_t& bstrSrc
);

_variant_t(
   const wchar_t *wstrSrc
);

_variant_t(
   const char* strSrc
);

_variant_t(
   IDispatch* pDispSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   bool bSrc
) throw( );

_variant_t(
   IUnknown* pIUknownSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   const DECIMAL& decSrc
) throw( );

_variant_t(
   BYTE bSrc
) throw( );

variant_t(
   char cSrc
) throw();

_variant_t(
   unsigned short usSrc
) throw();

_variant_t(
   unsigned long ulSrc
) throw();

_variant_t(
   int iSrc
) throw();

_variant_t(
   unsigned int uiSrc
) throw();

_variant_t(
   __int64 i8Src
) throw();

_variant_t(
   unsigned __int64 ui8Src
) throw();
```

#### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Objet `VARIANT` à copier dans le nouvel objet `_variant_t`.

*pVarSrc*<br/>
Pointeur vers un `VARIANT` objet à copier dans le nouvel `_variant_t` objet.

*var_t_Src*<br/>
Objet `_variant_t` à copier dans le nouvel objet `_variant_t`.

*fCopy*<br/>
Si **`false`** la `VARIANT` valeur est, l’objet fourni est attaché au nouvel `_variant_t` objet sans effectuer de nouvelle copie par `VariantCopy` .

*ISrc, sSrc*<br/>
Valeur entière à copier dans le nouvel objet `_variant_t`.

*vtSrc*<br/>
`VARTYPE`Pour le nouvel `_variant_t` objet.

*fltSrc, dblSrc*<br/>
Valeur numérique à copier dans le nouvel objet `_variant_t`.

*cySrc*<br/>
Objet `CY` à copier dans le nouvel objet `_variant_t`.

*bstrSrc*<br/>
Objet `_bstr_t` à copier dans le nouvel objet `_variant_t`.

*strSrc, wstrSrc*<br/>
Chaîne à copier dans le nouvel objet `_variant_t`.

*bSrc*<br/>
**`bool`** Valeur à copier dans le nouvel `_variant_t` objet.

*pIUknownSrc*<br/>
Pointeur d’interface COM vers un objet VT_UNKNOWN à encapsuler dans le nouvel `_variant_t` objet.

*pDispSrc*<br/>
Pointeur d’interface COM vers un objet VT_DISPATCH à encapsuler dans le nouvel `_variant_t` objet.

*decSrc*<br/>
Valeur `DECIMAL` à copier dans le nouvel objet `_variant_t`.

*bSrc*<br/>
Valeur `BYTE` à copier dans le nouvel objet `_variant_t`.

*cSrc*<br/>
**`char`** Valeur à copier dans le nouvel `_variant_t` objet.

*usSrc*<br/>
**`unsigned short`** Valeur à copier dans le nouvel `_variant_t` objet.

*ulSrc*<br/>
**`unsigned long`** Valeur à copier dans le nouvel `_variant_t` objet.

*iSrc*<br/>
**`int`** Valeur à copier dans le nouvel `_variant_t` objet.

*uiSrc*<br/>
**`unsigned int`** Valeur à copier dans le nouvel `_variant_t` objet.

*i8Src*<br/>
**`__int64`** Valeur à copier dans le nouvel `_variant_t` objet.

*ui8Src*<br/>
Valeur **__int64 non signée** à copier dans le nouvel `_variant_t` objet.

## <a name="remarks"></a>Notes

- **_variant_t ()** Construit un objet vide `_variant_t` , `VT_EMPTY` .

- **_variant_t (variante&** *varSrc***)** Construit un `_variant_t` objet à partir d’une copie de l' `VARIANT` objet.     Le type variant est conservé.

- **_variant_t (variant** <strong>\*</strong> *pVarSrc***)** construit un `_variant_t` objet à partir d’une copie de l' `VARIANT` objet.     Le type variant est conservé.

- **_variant_t (_variant_t&** *var_t_Src***)** Construit un `_variant_t` objet à partir d’un autre `_variant_t` objet.     Le type variant est conservé.

- **_variant_t (variant&** *varSrc* **, bool** `fCopy` **)** construit un `_variant_t` objet à partir d’un `VARIANT` objet existant.       Si *fCopy* a **`false`** la valeur, l’objet **Variant** est attaché au nouvel objet sans faire de copie.

- **_variant_t (Short***sSrc* **, VarType** `vtSrc` **= VT_I2)** construit un `_variant_t` objet de type VT_I2 ou VT_BOOL à partir d’une **`short`** valeur entière.       Tout autre `VARTYPE` résultat dans une erreur E_INVALIDARG.

- **_variant_t (long** `lSrc` **, VarType** `vtSrc` **= VT_I4)** construit un `_variant_t` objet de type VT_I4, VT_BOOL ou VT_ERROR à partir d’une **`long`** valeur entière.       Tout autre `VARTYPE` résultat dans une erreur E_INVALIDARG.

- **_variant_t (float** `fltSrc` **)** construit un `_variant_t` objet de type VT_R4 à partir d’une **`float`** valeur numérique.    

- **_variant_t (double** `dblSrc` **, VarType** `vtSrc` **= VT_R8)** construit un `_variant_t` objet de type VT_R8 ou VT_DATE à partir d’une **`double`** valeur numérique.       Tout autre `VARTYPE` résultat dans une erreur E_INVALIDARG.

- **_variant_t (CY&** `cySrc` **)** construit un `_variant_t` objet de type VT_CY à partir d’un `CY` objet.    

- **_variant_t (_bstr_t&** `bstrSrc` **)** construit un `_variant_t` objet de type VT_BSTR à partir d’un `_bstr_t` objet.     Un nouvel objet `BSTR` est alloué.

- **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc*  **)** construit un `_variant_t` objet de type VT_BSTR à partir d’une chaîne Unicode. Un nouvel objet `BSTR` est alloué.

- **_variant_t (char** <strong>\*</strong> `strSrc` **)** Construit un `_variant_t` objet de type VT_BSTR à partir d’une chaîne.     Un nouvel objet `BSTR` est alloué.

- **_variant_t (bool** `bSrc` **)** construit un `_variant_t` objet de type VT_BOOL à partir d’une **`bool`** valeur.    

- **_variant_t (IUnknown** <strong>\*</strong> `pIUknownSrc` **, bool** `fAddRef` **= true)** Construit un `_variant_t` objet de type VT_UNKNOWN à partir d’un pointeur d’interface com.       Si `fAddRef` est **`true`** , `AddRef` est appelé sur le pointeur d’interface fourni pour faire correspondre l’appel à `Release` qui se produit lorsque l' `_variant_t` objet est détruit. C’est à vous d’appeler `Release` sur le pointeur d’interface fourni. Si `fAddRef` est **`false`** , ce constructeur prend la propriété du pointeur d’interface fourni ; n’appelez pas `Release` sur le pointeur d’interface fourni.

- **_variant_t (IDispatch** <strong>\*</strong> `pDispSrc` **, bool** `fAddRef` **= true)** Construit un `_variant_t` objet de type VT_DISPATCH à partir d’un pointeur d’interface com.       Si `fAddRef` est **`true`** , `AddRef` est appelé sur le pointeur d’interface fourni pour faire correspondre l’appel à `Release` qui se produit lorsque l' `_variant_t` objet est détruit. C’est à vous d’appeler `Release` sur le pointeur d’interface fourni. Si `fAddRef` est **`false`** , ce constructeur prend la propriété du pointeur d’interface fourni ; n’appelez pas `Release` sur le pointeur d’interface fourni.

- **_variant_t (Decimal&** `decSrc` **)** construit un `_variant_t` objet de type VT_DECIMAL à partir d’une `DECIMAL` valeur.    

- **_variant_t (Byte** `bSrc` **)** construit un `_variant_t` objet de type `VT_UI1` à partir d’une `BYTE` valeur.    

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
