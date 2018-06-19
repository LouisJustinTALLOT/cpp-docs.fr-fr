---
title: Points de connexion ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 179f4329d55261d71d3d122e6a2601ce7e805c0f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354666"
---
# <a name="atl-connection-points"></a>ATL, points de connexion
Un objet connectable est un objet qui prend en charge les interfaces sortantes. Une interface sortante permet à l'objet de communiquer avec un client. Pour chaque interface sortante, l'objet connectable expose un point de connexion. Chaque interface sortante est implémentée par un client sur un objet appelé récepteur.  
  
 ![Points de connexion](../atl/media/vc2zw31.gif "vc2zw31")  
  
 Chaque point de connexion prend en charge la [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) interface. L’objet connectable expose ses points de connexion au client via le [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857) interface.  
  
## <a name="in-this-section"></a>Dans cette section  
 [ATL, classes de point de connexion](../atl/atl-connection-point-classes.md)  
 Décrit brièvement les classes ATL qui prennent en charge les points de connexion.  
  
 [Ajout de points de connexion à un objet](../atl/adding-connection-points-to-an-object.md)  
 Décrit les étapes à suivre pour ajouter des points de connexion à un objet.  
  
 [ATL, exemple de point de connexion](../atl/atl-connection-point-example.md)  
 Présente un exemple de déclaration de point de connexion.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)

