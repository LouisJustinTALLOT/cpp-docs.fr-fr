---
title: IUnknown | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c02018ee3cefb1b98c2df850d44578cf3a092c64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355837"
---
# <a name="iunknown"></a>IUnknown
[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) est l’interface de base de toutes les autres interfaces COM.  Cette interface définit trois méthodes : [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521), [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), et [version](http://msdn.microsoft.com/library/windows/desktop/ms682317). [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) permet à un utilisateur de l’interface demander l’objet d’un pointeur vers un autre de ses interfaces. [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) et [version](http://msdn.microsoft.com/library/windows/desktop/ms682317) implémenter le décompte de références sur l’interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à COM](../atl/introduction-to-com.md)   
 [IUnknown et héritage de l’Interface](http://msdn.microsoft.com/library/windows/desktop/ms692713)

