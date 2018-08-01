---
title: _com_ptr_t::Detach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf38e433f7042707b502a4cba2088db9412adb29
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405832"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Section spécifique à Microsoft**  
  
 Extrait et retourne le pointeur d'interface encapsulé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Interface* Detach( ) throw( );  
```  
  
## <a name="remarks"></a>Notes  
 Extrait et retourne le pointeur d’interface encapsulé, puis efface le stockage du pointeur encapsulé avec la valeur NULL. Cela supprime le pointeur d'interface de l'encapsulation. Il vous incombe d’appeler `Release` sur le pointeur d’interface retourné.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_ptr_t, classe](../cpp/com-ptr-t-class.md)