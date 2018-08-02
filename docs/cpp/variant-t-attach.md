---
title: _variant_t::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 567a3387e79244443b784549d6223a14f78103ce
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464678"
---
# <a name="varianttattach"></a>_variant_t::Attach
**Section spécifique à Microsoft**  
  
 Attache un `VARIANT` de l’objet dans le **_variant_t** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Attach(VARIANT& varSrc);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *varSrc*  
 Un `VARIANT` objet à attacher à cet **_variant_t** objet.  
  
## <a name="remarks"></a>Notes  
 Prend possession de la `VARIANT` en l’encapsulant. Cette fonction membre libère tout encapsulé existant `VARIANT`, puis copie fourni `VARIANT`et définit sa `VARTYPE` avec la valeur VT_EMPTY s’assurer que ses ressources peuvent uniquement être libérées par le **_variant_t** destructeur.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_variant_t, classe](../cpp/variant-t-class.md)