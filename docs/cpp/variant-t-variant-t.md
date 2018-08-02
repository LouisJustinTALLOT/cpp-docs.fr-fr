---
title: _variant_t::_variant_t | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::_variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ef7551047449167ff60372da146618fbdc4e564
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464160"
---
# <a name="varianttvariantt"></a>_variant_t::_variant_t
**Section spécifique à Microsoft**  
  
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
 *varSrc*  
 Objet `VARIANT` à copier dans le nouvel objet `_variant_t`.  
  
 *pVarSrc*  
 Pointeur vers un `VARIANT` objet doit être copié dans le nouveau `_variant_t` objet.  
  
 *var_t_Src*  
 Objet `_variant_t` à copier dans le nouvel objet `_variant_t`.  
  
 *fCopy*  
 Si **false**, fourni `VARIANT` objet est attaché à la nouvelle `_variant_t` objet sans avoir à effectuer une nouvelle copie par `VariantCopy`.  
  
 *ISrc, sSrc*  
 Valeur entière à copier dans le nouvel objet `_variant_t`.  
  
 *vtSrc*  
 Le `VARTYPE` pour le nouveau `_variant_t` objet.  
  
 *fltSrc, dblSrc*  
 Valeur numérique à copier dans le nouvel objet `_variant_t`.  
  
 *cySrc*  
 Objet `CY` à copier dans le nouvel objet `_variant_t`.  
  
 *bstrSrc*  
 Objet `_bstr_t` à copier dans le nouvel objet `_variant_t`.  
  
 *strSrc, wstrSrc*  
 Chaîne à copier dans le nouvel objet `_variant_t`.  
  
 *bSrc*  
 Un **bool** valeur doit être copié dans le nouveau `_variant_t` objet.  
  
 *pIUknownSrc*  
 Pointeur d’interface COM à un objet VT_UNKNOWN à encapsuler dans le nouveau `_variant_t` objet.  
  
 *pDispSrc*  
 Pointeur d’interface COM à un objet VT_DISPATCH à encapsuler dans le nouveau `_variant_t` objet.  
  
 *decSrc*  
 Valeur `DECIMAL` à copier dans le nouvel objet `_variant_t`.  
  
 *bSrc*  
 Valeur `BYTE` à copier dans le nouvel objet `_variant_t`.  
  
 *cSrc*  
 Un **char** valeur doit être copié dans le nouveau `_variant_t` objet.  
  
 *usSrc*  
 Un **unsigned short** valeur doit être copié dans le nouveau `_variant_t` objet.  
  
 *ulSrc*  
 Un **long non signé** valeur doit être copié dans le nouveau `_variant_t` objet.  
  
 *iSrc*  
 Un **int** valeur doit être copié dans le nouveau `_variant_t` objet.  
  
 *uiSrc*  
 Un **unsigned int** valeur doit être copié dans le nouveau `_variant_t` objet.  
  
 *i8Src*  
 Un **__int64** valeur doit être copié dans le nouveau `_variant_t` objet.  
  
 *ui8Src*  
 Un **unsigned __int64** valeur doit être copié dans le nouveau `_variant_t` objet.  
  
## <a name="remarks"></a>Notes  
  
-   **_variant_t ()** construit vide `_variant_t` objet, `VT_EMPTY`.  
  
-   **_variant_t (VARIANT &***varSrc***)** construit un `_variant_t` objet à partir d’une copie de la `VARIANT` objet.     Le type variant est conservé.  
  
-   **_variant_t (VARIANT\****pVarSrc***)** construit un `_variant_t` objet à partir d’une copie de la `VARIANT` objet.     Le type variant est conservé.  
  
-   **_variant_t (_variant_t &***var_t_Src***)** construit un `_variant_t` objet à partir d’un autre `_variant_t` objet.     Le type variant est conservé.  
  
-   **_variant_t (VARIANT &***varSrc* **, bool**`fCopy`**)** construit un `_variant_t` objet depuis une `VARIANT` objet.       Si *fCopy* est **false**, le **VARIANT** objet est attaché au nouvel objet sans avoir à effectuer une copie.  
  
-   **_variant_t (short***sSrc* **, VARTYPE**`vtSrc`**= VT_I2)** construit un `_variant_t` objet de type VT_I2 ou VT_BOOL à partir d’un **court** valeur entière.       N’importe quel autre `VARTYPE` entraîne une erreur E_INVALIDARG.  
  
-   **_variant_t (long** `lSrc` **, VARTYPE**`vtSrc`**= VT_I4)** construit un `_variant_t` objet de type VT_I4, VT_BOOL ou VT_ERROR à partir d’un **long**  valeur entière.       N’importe quel autre `VARTYPE` entraîne une erreur E_INVALIDARG.  
  
-   **_variant_t (float**`fltSrc`**)** construit un `_variant_t` objet de type VT_R4 à partir d’un **float** valeur numérique.      
  
-   **_variant_t (double** `dblSrc` **, VARTYPE**`vtSrc`**= VT_R8)** construit un `_variant_t` objet de type VT_R8 ou VT_DATE à partir d’un **double** valeur numérique.       N’importe quel autre `VARTYPE` entraîne une erreur E_INVALIDARG.  
  
-   **_variant_t (CY &**`cySrc`**)** construit un `_variant_t` objet de type VT_CY à partir d’un `CY` objet.      
  
-   **_variant_t (_bstr_t &**`bstrSrc`**)** construit un `_variant_t` objet de type VT_BSTR à partir d’un `_bstr_t` objet.     Un nouvel objet `BSTR` est alloué.  
  
-   **_variant_t (wchar_t \***  *wstrSrc***)** construit un `_variant_t` objet de type VT_BSTR à partir d’une chaîne Unicode.   Un nouvel objet `BSTR` est alloué.  
  
-   **_variant_t (char\***`strSrc`**)** construit un `_variant_t` objet de type VT_BSTR à partir d’une chaîne.     Un nouvel objet `BSTR` est alloué.  
  
-   **_variant_t (bool**`bSrc`**)** construit un `_variant_t` objet de type VT_BOOL à partir d’un **bool** valeur.      
  
-   **_variant_t (IUnknown\***  `pIUknownSrc` **, bool**`fAddRef`**= true)** construit un `_variant_t` objet de type VT_UNKNOWN à partir d’un pointeur d’interface COM .       Si `fAddRef` est **true**, puis `AddRef` est appelée sur le pointeur d’interface fourni pour faire correspondre l’appel à `Release` qui se produit lorsque le `_variant_t` objet est détruit. Il vous incombe d’appeler `Release` sur le pointeur d’interface fourni. Si `fAddRef` est **false**, ce constructeur prend possession du pointeur d’interface fourni ; n’appelez pas `Release` sur le pointeur d’interface fourni.  
  
-   **_variant_t (IDispatch\***  `pDispSrc` **, bool**`fAddRef`**= true)** construit un `_variant_t` objet de type VT_DISPATCH à partir d’une interface COM pointeur.       Si `fAddRef` est **true**, puis `AddRef` est appelée sur le pointeur d’interface fourni pour faire correspondre l’appel à `Release` qui se produit lorsque le `_variant_t` objet est détruit. Il vous incombe d’appeler `Release` sur le pointeur d’interface fourni. Si `fAddRef` est **false**, ce constructeur prend possession du pointeur d’interface fourni ; n’appelez pas `Release` sur le pointeur d’interface fourni.  
  
-   **_variant_t (DECIMAL &**`decSrc`**)** construit un `_variant_t` objet de type VT_DECIMAL à partir d’un `DECIMAL` valeur.      
  
-   **_variant_t (BYTE**`bSrc`**)** construit un `_variant_t` objet de type `VT_UI1` à partir d’un `BYTE` valeur.      
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_variant_t, classe](../cpp/variant-t-class.md)