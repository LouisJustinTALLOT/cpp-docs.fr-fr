---
title: Hstringreference::hstringreference, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7dce8c6fca14ad26665bf4868681234374c20f85
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608142"
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference, constructeur
Initialise une nouvelle instance de la **HStringReference** classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest],   
                 unsigned int len) throw();  
  
HStringReference(HStringReference&& other) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 *sizeDest*  
 Un paramètre de modèle qui spécifie la taille de la destination **HStringReference** mémoire tampon.  
  
 *str*  
 Une référence à une chaîne à caractères larges.  
  
 *Len*  
 La longueur maximale de la *str* mémoire tampon de paramètre à utiliser dans cette opération. Si le *len* paramètre n’est pas spécifié, l’intégralité de *str* paramètre est utilisé. Si *len* est supérieur à *sizeDest*, *len* a la valeur *sizeDest*-1.  
  
 *other*  
 Un autre **HStringReference** objet.  
  
## <a name="remarks"></a>Notes  
 Le premier constructeur initialise un nouveau **HStringReference** objet la même taille que le paramètre *str*.  
  
 Le deuxième constructeur initialise un nouveau **HStringReference** de l’objet qui le specifeid de taille par paramètre *len*.  
  
 Le troisième constructeur initialise un nouveau **HStringReference** objet à la valeur de la *autres* paramètre et détruit le *autres* paramètre.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HStringReference, classe](../windows/hstringreference-class.md)