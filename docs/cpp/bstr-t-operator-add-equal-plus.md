---
title: _bstr_t::operator +=, + | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aad73939b8fd011fd6e1c9bf16f8dfe6eb303ff3
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405741"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +
**Section spécifique à Microsoft**  
  
 Ajoute des caractères à la fin de l'objet `_bstr_t` ou concatène deux chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_bstr_t& operator+=( const _bstr_t& s1 );  
_bstr_t operator+( const _bstr_t& s1 );  
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);  
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *s1*  
 Objet `_bstr_t`.  
  
 *s2*  
 Chaîne multioctet.  
  
 *S3*  
 Chaîne Unicode.  
  
## <a name="remarks"></a>Notes  
 Ces opérateurs exécutent une concaténation de chaînes :  
  
-   **operator += (***s1***)** ajoute les caractères dans encapsulé `BSTR` de *s1* à la fin de encapsulédecetobjet`BSTR`.  
  
-   **operator + (***s1***)** retourne le nouvel `_bstr_t` qui est formé en concaténant de cet objet `BSTR` avec celui de *s1*.  
  
-   **operator + (***s2***&#124;***s1***)** retourne un nouvel `_bstr_t` qui est formé en concaténant une chaîne multioctet *s2*, converti en Unicode, avec le `BSTR` encapsulé dans *s1*.          
  
-   **operator + (***s3* **,***s1***)** retourne un nouvel `_bstr_t` formé en concaténant une chaîne Unicode *s3* avec la `BSTR` encapsulé dans *s1*.        
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_bstr_t, classe](../cpp/bstr-t-class.md)