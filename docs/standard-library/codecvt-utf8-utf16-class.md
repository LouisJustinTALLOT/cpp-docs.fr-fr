---
title: codecvt_utf8_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::cvt_utf8_utf16
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
ms.openlocfilehash: 879ebe6a75d76a84ef4250b95c41e02eccba5517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458641"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

Représente une facette [locale](../standard-library/locale-class.md) qui effectue la conversion entre des caractères larges codés au format UTF-16 et un flux d’octets codé au format UTF-8.

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

## <a name="requirements"></a>Configuration requise

En- \<tête: codecvt >

Espace de noms: STD
