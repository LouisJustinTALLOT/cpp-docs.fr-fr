---
title: _variant_t::SetString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 090fd7ed027738ebe7bc9276e3b3f124b9212c4a
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463465"
---
# <a name="varianttsetstring"></a>_variant_t::SetString
**Section spécifique à Microsoft**  
  
 Assigne une chaîne à cet objet `_variant_t`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void SetString(const char* pSrc);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pSrc*  
 Pointeur vers la chaîne de caractères.  
  
## <a name="remarks"></a>Notes  
 Convertit une chaîne de caractères ANSI en chaîne Unicode `BSTR` et l'assigne à cet objet `_variant_t`.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_variant_t, classe](../cpp/variant-t-class.md)