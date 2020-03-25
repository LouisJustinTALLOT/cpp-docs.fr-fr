---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: fff116ef04967a1887eaa075d92d3ea0283d5427
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187529"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Section spécifique de Microsoft**

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
Pointeur vers un objet `VARIANT` à copier dans le nouvel objet `_variant_t`.

*var_t_Src*<br/>
Objet `_variant_t` à copier dans le nouvel objet `_variant_t`.

*fCopy*<br/>
Si la **valeur est false**, l’objet `VARIANT` fourni est attaché au nouvel objet `_variant_t` sans effectuer de nouvelle copie par `VariantCopy`.

*ISrc, sSrc*<br/>
Valeur entière à copier dans le nouvel objet `_variant_t`.

*vtSrc*<br/>
`VARTYPE` pour le nouvel objet `_variant_t`.

*fltSrc, dblSrc*<br/>
Valeur numérique à copier dans le nouvel objet `_variant_t`.

*cySrc*<br/>
Objet `CY` à copier dans le nouvel objet `_variant_t`.

*bstrSrc*<br/>
Objet `_bstr_t` à copier dans le nouvel objet `_variant_t`.

*strSrc, wstrSrc*<br/>
Chaîne à copier dans le nouvel objet `_variant_t`.

*bSrc*<br/>
Valeur **bool** à copier dans le nouvel objet `_variant_t`.

*pIUknownSrc*<br/>
Pointeur d’interface COM vers un objet VT_UNKNOWN à encapsuler dans le nouvel objet `_variant_t`.

*pDispSrc*<br/>
Pointeur d’interface COM vers un objet VT_DISPATCH à encapsuler dans le nouvel objet `_variant_t`.

*decSrc*<br/>
Valeur `DECIMAL` à copier dans le nouvel objet `_variant_t`.

*bSrc*<br/>
Valeur `BYTE` à copier dans le nouvel objet `_variant_t`.

*cSrc*<br/>
Valeur **char** à copier dans le nouvel objet `_variant_t`.

*usSrc*<br/>
Valeur **short non signée** à copier dans le nouvel objet `_variant_t`.

*ulSrc*<br/>
Valeur **long non signée** à copier dans le nouvel objet `_variant_t`.

*iSrc*<br/>
Valeur **int** à copier dans le nouvel objet `_variant_t`.

*uiSrc*<br/>
Valeur **int non signée** à copier dans le nouvel objet `_variant_t`.

*i8Src*<br/>
Valeur **__int64** à copier dans le nouvel objet `_variant_t`.

*ui8Src*<br/>
Valeur **__int64 non signée** à copier dans le nouvel objet `_variant_t`.

## <a name="remarks"></a>Notes

- **_variant_t ()** Construit un objet `_variant_t` vide, `VT_EMPTY`.

- **_variant_t (variante &**  *varSrc*  **)** Construit un objet `_variant_t` à partir d’une copie de l’objet `VARIANT`. Le type variant est conservé.

- **_variant_t (variante** <strong>\*</strong> *pVarSrc* **)** Construit un objet `_variant_t` à partir d’une copie de l’objet `VARIANT`. Le type variant est conservé.

- **_variant_t (_variant_t &**  *var_t_Src*  **)** Construit un objet `_variant_t` à partir d’un autre objet `_variant_t`. Le type variant est conservé.

- **_variant_t (variant &** *varSrc* **, bool**`fCopy` **)** Construit un objet `_variant_t` à partir d’un objet `VARIANT` existant. Si *fCopy* a la **valeur false**, l’objet **Variant** est attaché au nouvel objet sans faire de copie.

- **_variant_t (Short***sSrc* **, VarType**`vtSrc` **= VT_I2)** Construit un objet `_variant_t` de type VT_I2 ou VT_BOOL à partir d’une valeur entière **short** . Tout autre `VARTYPE` entraîne une erreur de E_INVALIDARG.

- **_variant_t (long**`lSrc` **, VARTYPE**`vtSrc` **= VT_I4)** Construit un objet `_variant_t` de type VT_I4, VT_BOOL ou VT_ERROR à partir d’une valeur entière **longue** . Tout autre `VARTYPE` entraîne une erreur de E_INVALIDARG.

- **_variant_t (float**`fltSrc` **)** Construit un objet `_variant_t` de type VT_R4 à partir d’une valeur numérique à **virgule flottante** .

- **_variant_t (double**`dblSrc` **, VARTYPE**`vtSrc` **= VT_R8)** Construit un objet `_variant_t` de type VT_R8 ou VT_DATE à partir d’une valeur numérique **double** . Tout autre `VARTYPE` entraîne une erreur de E_INVALIDARG.

- **_variant_t (ca &** `cySrc` **)** Construit un objet `_variant_t` de type VT_CY à partir d’un objet `CY`.

- **_variant_t (_bstr_t &** `bstrSrc` **)** Construit un objet `_variant_t` de type VT_BSTR à partir d’un objet `_bstr_t`. Un nouvel objet `BSTR` est alloué.

- **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc*  **)** Construit un objet `_variant_t` de type VT_BSTR à partir d’une chaîne Unicode. Un nouvel objet `BSTR` est alloué.

- **_variant_t (char** <strong>\*</strong>`strSrc` **)** Construit un objet `_variant_t` de type VT_BSTR à partir d’une chaîne. Un nouvel objet `BSTR` est alloué.

- **_variant_t (bool**`bSrc` **)** Construit un objet `_variant_t` de type VT_BOOL à partir d’une valeur **bool** .

- **_variant_t (IUnknown** <strong>\*</strong>`pIUknownSrc` **, bool**`fAddRef` **= true)** Construit un objet `_variant_t` de type VT_UNKNOWN à partir d’un pointeur d’interface COM. Si `fAddRef` a la **valeur true**, `AddRef` est appelé sur le pointeur d’interface fourni pour faire correspondre l’appel à `Release` qui se produira lorsque l’objet `_variant_t` sera détruit. Il vous revient d’appeler `Release` sur le pointeur d’interface fourni. Si `fAddRef` a la **valeur false**, ce constructeur prend la propriété du pointeur d’interface fourni ; n’appelez pas `Release` sur le pointeur d’interface fourni.

- **_variant_t (IDispatch** <strong>\*</strong>`pDispSrc` **, bool**`fAddRef` **= true)** Construit un objet `_variant_t` de type VT_DISPATCH à partir d’un pointeur d’interface COM. Si `fAddRef` a la **valeur true**, `AddRef` est appelé sur le pointeur d’interface fourni pour faire correspondre l’appel à `Release` qui se produira lorsque l’objet `_variant_t` sera détruit. Il vous revient d’appeler `Release` sur le pointeur d’interface fourni. Si `fAddRef` a la **valeur false**, ce constructeur prend la propriété du pointeur d’interface fourni ; n’appelez pas `Release` sur le pointeur d’interface fourni.

- **_variant_t (décimal &** `decSrc` **)** Construit un objet `_variant_t` de type VT_DECIMAL à partir d’une valeur de `DECIMAL`.

- **_variant_t (BYTE**`bSrc` **)** Construit un objet `_variant_t` de type `VT_UI1` à partir d’une valeur de `BYTE`.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)
