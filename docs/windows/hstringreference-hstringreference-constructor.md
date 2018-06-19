---
title: Hstringreference::hstringreference, constructeur | Documents Microsoft
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
ms.openlocfilehash: dc88ea32d4384b36559a4a10da0a5975345bf0d7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876005"
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HStringReference, classe](../windows/hstringreference-class.md)