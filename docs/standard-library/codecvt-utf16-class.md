---
title: codecvt_utf16 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa4147f28e7b780e9d916526f0e46e91432fd1ce
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714231"
---
# <a name="codecvtutf16"></a>codecvt_utf16

Représente une facette [locale](../standard-library/locale-class.md) qui effectue la conversion entre des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets codé au format UTF-16LE ou UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Paramètres

*Elem*<br/>
Type d'élément à caractères larges.

*Maxcode*<br/>
Nombre maximal de caractères pour la facette de paramètres régionaux.

*Mode*<br/>
Informations de configuration pour les facettes de paramètres régionaux.

## <a name="remarks"></a>Notes

Cette classe de modèle convertit des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets codé au format UTF-16LE (si Mode & little_endian) ou UTF-16BE dans le cas contraire.

Le flux d’octets doit être écrit dans un fichier binaire. Il peut être endommagé s’il est écrit dans un fichier texte.

## <a name="requirements"></a>Configuration requise

En-tête : \<codecvt >

Namespace : std