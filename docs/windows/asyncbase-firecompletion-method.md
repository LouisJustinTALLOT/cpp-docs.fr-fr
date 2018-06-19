---
title: Asyncbase::firecompletion, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireCompletion
dev_langs:
- C++
helpviewer_keywords:
- FireCompletion method
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0cd18d340a11575ed9f6f52d92a5910dcee1faec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859733"
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion, méthode
Appelle le Gestionnaire d’événements de fin, ou réinitialise le délégué de progression interne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void FireCompletion(  
   void  
) override;  
  
virtual void FireCompletion();  
```  
  
## <a name="remarks"></a>Notes  
 La première version de FireCompletion() réinitialise la variable de délégué progression interne. La deuxième version appelle le Gestionnaire d’événements de fin si l’opération asynchrone est terminée.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)