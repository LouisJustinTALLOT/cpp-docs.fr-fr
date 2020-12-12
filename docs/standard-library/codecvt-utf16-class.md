---
description: 'En savoir plus sur : codecvt_utf16'
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: 264324d0f827e8999b065205010874ebf62ca501
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325086"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

Représente une facette de [paramètres régionaux](../standard-library/locale-class.md) qui effectue la conversion entre des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets encodé au format UTF-16LE ou UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Paramètres

*Elem*\
Type d'élément à caractères larges.

*Maxcode*\
Nombre maximal de caractères pour la facette de paramètres régionaux.

*Mode*\
Informations de configuration pour les facettes de paramètres régionaux.

## <a name="remarks"></a>Notes

Ce modèle de classe convertit des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets encodé au format UTF-16LE, si le mode & little_endian ou UTF-16BE dans le cas contraire.

Le flux d’octets doit être écrit dans un fichier binaire. Il peut être endommagé s’il est écrit dans un fichier texte.

## <a name="requirements"></a>Spécifications

En-tête : \<codecvt>

Espace de noms : std
