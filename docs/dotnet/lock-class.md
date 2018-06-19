---
title: Lock, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a860f79b740e0f34eef33b7a96e0236835f1f6b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129695"
---
# <a name="lock-class"></a>lock, classe
Cette classe permet d’automatiser l’acquisition un d'verrou de synchroniser l’accès à un objet à partir de plusieurs threads.  Lors de la construction il acquiert le verrou et quand elle détruit libère le verrou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>Notes  
 `lock` est disponible uniquement pour les objets CLR et peut uniquement être utilisé dans le code CLR.  
  
 En interne, la classe de verrou d’utilise <xref:System.Threading.Monitor> pour synchroniser l’accès. Consultez cette rubrique pour plus d’informations sur la synchronisation.  
  
## <a name="requirements"></a>Spécifications  
 **Fichier d’en-tête** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Voir aussi  
 [lock](../dotnet/lock.md)   
 [lock, membres](../dotnet/lock-members.md)