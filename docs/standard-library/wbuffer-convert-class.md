---
description: 'En savoir plus sur : classe wbuffer_convert'
title: wbuffer_convert, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: 1aa7258c3cc0a4f78a749f655e9cfb7cd4957378
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187843"
---
# <a name="wbuffer_convert-class"></a>wbuffer_convert, classe

Décrit une mémoire tampon de flux qui contrôle la transmission des éléments vers et à partir d'une mémoire tampon de flux d'octets.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Paramètres

*Codecvt*\
La facette [locale](../standard-library/locale-class.md) qui représente l’objet de conversion.

*Elem*\
Type d'élément à caractères larges.

*Caractéristiques*\
Caractéristiques associées à *Elem*.

## <a name="remarks"></a>Notes

Ce modèle de classe décrit une mémoire tampon de flux qui contrôle la transmission d’éléments de type `_Elem` , dont les caractéristiques sont décrites par la classe `Traits` , vers et à partir d’une mémoire tampon de flux d’octets de type `std::streambuf` .

La conversion entre une séquence de valeurs `Elem` et des séquences multioctets est effectuée par un objet de classe `Codecvt<Elem, char, std::mbstate_t>`, qui répond aux exigences de la facette de conversion de code standard `std::codecvt<Elem, char, std::mbstate_t>`.

Un objet de ce modèle de classe stocke les éléments suivants :

- un pointeur vers sa mémoire tampon de flux d'octets sous-jacente ;

- un pointeur vers l’objet de conversion alloué (qui est libéré quand l’objet [wbuffer_convert](../standard-library/wbuffer-convert-class.md)
