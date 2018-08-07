---
title: Hstring::makereference, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 673d5b10706580303f179ee453495b581d96eda3
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608333"
---
# <a name="hstringmakereference-method"></a>HString::MakeReference, méthode
Crée un `HStringReference` objet à partir d’un paramètre de chaîne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[ sizeDest]);  
  
    template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[sizeDest],   
              unsigned int len);  
```  
  
### <a name="parameters"></a>Paramètres  
 *sizeDest*  
 Un paramètre de modèle qui spécifie la taille de la destination `HStringReference` mémoire tampon.  
  
 *str*  
 Une référence à une chaîne à caractères larges.  
  
 *Len*  
 La longueur maximale de la *str* mémoire tampon de paramètre à utiliser dans cette opération. Si le *len* paramètre n’est pas spécifié, l’intégralité de *str* paramètre est utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Un `HStringReference` objet dont la valeur est identique à celui du texte spécifié *str* paramètre.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)