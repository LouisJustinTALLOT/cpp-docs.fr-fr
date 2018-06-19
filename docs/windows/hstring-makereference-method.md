---
title: Hstring::makereference, méthode | Documents Microsoft
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
ms.openlocfilehash: e30b3ea3c6b791eb654a6fbbe91b3c87353f31c1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882639"
---
# <a name="hstringmakereference-method"></a>HString::MakeReference, méthode
Crée un objet HStringReference à partir d’un paramètre de chaîne spécifiée.  
  
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
  
#### <a name="parameters"></a>Paramètres  
 `sizeDest`  
 Un paramètre de modèle qui spécifie la taille de la mémoire tampon HStringReference de destination.  
  
 `str`  
 Une référence à une chaîne à caractères larges.  
  
 `len`  
 La longueur maximale de la `str` mémoire tampon de paramètre à utiliser dans cette opération. Si le `len` paramètre n’est pas spécifié, l’ensemble `str` paramètre est utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Un objet HStringReference dont la valeur est identique à celui du texte spécifié `str` paramètre.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)