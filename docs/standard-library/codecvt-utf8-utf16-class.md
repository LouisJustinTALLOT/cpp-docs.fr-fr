---
description: 'En savoir plus sur : codecvt_utf8_utf16'
title: codecvt_utf8_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::cvt_utf8_utf16
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
ms.openlocfilehash: e80cdaa01ef77b9ce28a773eb4e05056220718a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325073"
---
# <a name="codecvt_utf8_utf16"></a>codecvt_utf8_utf16

Représente une facette de [paramètres régionaux](../standard-library/locale-class.md) qui effectue la conversion entre des caractères larges encodés au format UTF-16 et un flux d’octets encodé au format UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Paramètres

*Elem*\
Type d'élément à caractères larges.

*Maxcode*\
Nombre maximal de caractères pour la facette de paramètres régionaux.

*Mode*\
Informations de configuration pour les facettes de paramètres régionaux.

## <a name="remarks"></a>Notes

Le flux d’octets peut être écrit dans un fichier binaire ou un fichier texte.

## <a name="requirements"></a>Spécifications

En-tête : \<codecvt>

Espace de noms : std
