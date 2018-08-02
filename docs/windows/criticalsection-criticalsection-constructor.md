---
title: CriticalSection::CriticalSection, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 866159a4b3cbacae8b7ad09154fb93707fe4baac
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467350"
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection, constructeur
Initialise un objet de synchronisation qui est similaire à un objet mutex, mais peut être utilisé par uniquement les threads d’un processus unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *spinCount*  
 Nombre de spins pour l’objet de section critique. La valeur par défaut est 0.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les sections critiques et spincounts, consultez le `InitializeCriticalSectionAndSpinCount` fonctionner dans le **synchronisation** section de la documentation de l’API de Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [CriticalSection, classe](../windows/criticalsection-class.md)