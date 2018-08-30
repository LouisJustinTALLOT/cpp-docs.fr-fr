---
title: Interfaces (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1410a437d87b56b244eb4fcd711797c279bec446
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217881"
---
# <a name="interfaces-atl"></a>Interfaces (ATL)
Une interface est la méthode dans laquelle un objet expose ses fonctionnalités au monde extérieur. Dans COM, une interface est une table de pointeurs (comme un vtable C++) pour les fonctions implémentées par l’objet. La table représente l’interface, et les fonctions vers lequel il pointe sont les méthodes de cette interface. Un objet peut exposer autant d’interfaces qu’il le souhaite.  
  
 Chaque interface est basée sur l’interface COM fondamentale, [IUnknown](../atl/iunknown.md). Les méthodes de `IUnknown` autorisera la navigation vers d’autres interfaces exposées par l’objet.  
  
 En outre, chaque interface est dotée d’un unique ID d’interface (IID). Ce caractère unique facilite la charge du versioning. Une nouvelle version d’une interface est simplement une nouvelle interface, avec un nouveau IID.  
  
> [!NOTE]
>  IID pour les interfaces COM et OLE standards sont prédéfinies.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à COM](../atl/introduction-to-com.md)   
 [Interfaces et des objets COM](/windows/desktop/com/com-objects-and-interfaces)

