---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: 73177985727f4da5cf3ca4eb9e3cc3fb5976f76d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215278"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

Représente une facette [locale](../standard-library/locale-class.md) qui effectue la conversion entre des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets codé au format UTF-16LE ou UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Paramètres

\ *elem*
Type d'élément à caractères larges.

\ de *maxcode*
Nombre maximal de caractères pour la facette de paramètres régionaux.

\ du *mode*
Informations de configuration pour les facettes de paramètres régionaux.

## <a name="remarks"></a>Notes

Ce modèle de classe convertit des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets encodé au format UTF-16LE, si le mode & little_endian ou UTF-16BE dans le cas contraire.

Le flux d’octets doit être écrit dans un fichier binaire. Il peut être endommagé s’il est écrit dans un fichier texte.

## <a name="requirements"></a>Spécifications

En-tête : \<codecvt >

Espace de noms : std
