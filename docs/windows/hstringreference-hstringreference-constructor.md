---
title: Hstringreference::hstringreference, constructeur | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 398ea9403f784c30f8e015101c25b071f1d6fb29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference, constructeur
Initialise une nouvelle instance de la hstringreference, classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest],   
                 unsigned int len) throw();  
  
HStringReference(HStringReference&& other) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `sizeDest`  
 Un paramètre de modèle qui spécifie la taille de la mémoire tampon HStringReference de destination.  
  
 `str`  
 Une référence à une chaîne à caractères larges.  
  
 `len`  
 La longueur maximale de la `str` mémoire tampon de paramètre à utiliser dans cette opération. Si le `len` paramètre n’est pas spécifié, l’ensemble `str` paramètre est utilisé. Si `len` est supérieur à `sizeDest`, `len` a la valeur `sizeDest`-1.  
  
 `other`  
 Un autre objet HStringReference.  
  
## <a name="remarks"></a>Notes  
 Le premier constructeur initialise un nouvel objet de HStringReference la même taille que le paramètre `str`.  
  
 Le deuxième constructeur initialise un nouveau HStringReference de l’objet qui le specifeid taille par le paramètre `len`.  
  
 Le troisième constructeur initialise un nouvel objet HStringReference à la valeur de la `other` paramètre et puis détruit la `other` paramètre.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HStringReference, classe](../windows/hstringreference-class.md)