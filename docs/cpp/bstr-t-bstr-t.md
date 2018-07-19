---
title: _bstr_t::_bstr_t | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::_bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb2e870c7418c0d0a6cf3cd82bc0a8acb45466a0
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941263"
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
 *s1*  
 Objet `_bstr_t` à copier.  
  
 *s2*  
 Chaîne multioctet.  
  
 *S3*  
 Chaîne Unicode.  
  
 *var*  
 Un [_variant_t](../cpp/variant-t-class.md) objet.  
  
 *BSTR*  
 Objet `BSTR` existant.  
  
 *fCopy*  
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
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Construit un objet `_bstr_t` à partir d'un `BSTR` existant (par opposition à une chaîne `wchar_t*`). Si `fCopy` a la valeur false, le `BSTR` fourni est attaché au nouvel objet sans qu'une nouvelle copie soit effectuée avec `SysAllocString`.<br /><br /> Ce constructeur est utilisé par les fonctions wrapper dans les en-têtes de bibliothèque de types pour encapsuler et prendre possession d'un `BSTR` retourné par une méthode d'interface.|  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_bstr_t, classe](../cpp/bstr-t-class.md)   
 [_variant_t, classe](../cpp/variant-t-class.md)