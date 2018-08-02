---
title: ClassFactory::AddRef, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method
ms.assetid: 5b091785-dea4-42b6-a502-0db5fc7a5a2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1e01ceee3b889a1755fe272366ab66b32a79ae6f
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462691"
---
# <a name="classfactoryaddref-method"></a>ClassFactory::AddRef, méthode
Incrémente le décompte de références pour actuel **ClassFactory** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD_(  
   ULONG,  
   AddRef  
)();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ClassFactory, classe](../windows/classfactory-class.md)