---
title: _variant_t::Detach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs:
- C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f71257b369e7833f279c0f68ce33e0ec925ebf6b
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026258"
---
# <a name="varianttdetach"></a>_variant_t::Detach
**Section spécifique à Microsoft**  
  
 Détache encapsulé `VARIANT` objet à partir de ce `_variant_t` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
VARIANT Detach( );  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Encapsulé `VARIANT`.  
  
## <a name="remarks"></a>Notes  
 Extrait et retourne encapsulé `VARIANT`, puis efface alors cet `_variant_t` objet sans le détruire. Cette fonction membre supprime le `VARIANT` d’encapsulation et définit le `VARTYPE` de ce `_variant_t` objet avec la valeur VT_EMPTY. Il vous incombe de libérer retourné `VARIANT` en appelant le [VariantClear](http://msdn.microsoft.com/28741d81-8404-4f85-95d3-5c209ec13835) (fonction).  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_variant_t, classe](../cpp/variant-t-class.md)