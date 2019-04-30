---
title: codecvt_utf8
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf8
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
ms.openlocfilehash: 3e3ddeccac2c18eedb96746f1c442c6b42349783
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405245"
---
# <a name="codecvtutf8"></a>codecvt_utf8

Représente une facette [locale](../standard-library/locale-class.md) qui effectue la conversion entre des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets codé au format UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Paramètres

*Elem*<br/>
Type d'élément à caractères larges.

*Maxcode*<br/>
Nombre maximal de caractères pour la facette de paramètres régionaux.

*Mode*<br/>
Informations de configuration pour les facettes de paramètres régionaux.

## <a name="remarks"></a>Notes

Le flux d’octets peut être écrit dans un fichier binaire ou un fichier texte.

## <a name="requirements"></a>Configuration requise

En-tête : \<codecvt > \

Namespace : std
