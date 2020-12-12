---
description: 'En savoir plus sur : _bstr_t :: wchar_t *, _bstr_t :: char*'
title: _bstr_t::wchar_t *, _bstr_t::char*
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
ms.openlocfilehash: 278b122bbc208addab8e9a40e61300ce91a530cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278816"
---
# <a name="_bstr_twchar_t-_bstr_tchar"></a>_bstr_t::wchar_t\*, _bstr_t::char\*

**Spécifique à Microsoft**

Retourne les caractères BSTR sous la forme d'un tableau de caractères étroits ou larges.

## <a name="syntax"></a>Syntaxe

```
operator const wchar_t*( ) const throw( );
operator wchar_t*( ) const throw( );
operator const char*( ) const;
operator char*( ) const;
```

## <a name="remarks"></a>Notes

Ces opérateurs peuvent être utilisés pour extraire les données de type caractère encapsulées par l'objet `BSTR`. L'assignation d'une nouvelle valeur au pointeur retourné ne modifie pas les données BSTR d'origine.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _bstr_t](../cpp/bstr-t-class.md)
