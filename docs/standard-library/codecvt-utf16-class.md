---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: a84ca6da22825ca3fa7ab43e43a574fb05caa1a8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689823"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

Représente une facette [locale](../standard-library/locale-class.md) qui effectue la conversion entre des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets codé au format UTF-16LE ou UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Paramètres

@No__t_1 *elem*
Type d'élément à caractères larges.

@No__t_1 de *maxcode*
Nombre maximal de caractères pour la facette de paramètres régionaux.

@No__t_1 du *mode*
Informations de configuration pour les facettes de paramètres régionaux.

## <a name="remarks"></a>Notes

Ce modèle de classe convertit des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets encodé au format UTF-16LE, si le mode & LITTLE_ENDIAN ou UTF-16BE dans le cas contraire.

Le flux d’octets doit être écrit dans un fichier binaire. Il peut être endommagé s’il est écrit dans un fichier texte.

## <a name="requirements"></a>spécifications

En-tête : \<codecvt >

Espace de noms : STD