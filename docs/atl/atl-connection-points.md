---
title: ATL, points de connexion
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: 4d94396ef8839516d9bfee15a2611cce66baa6bd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297825"
---
# <a name="atl-connection-points"></a>ATL, points de connexion

Un objet connectable est un objet qui prend en charge les interfaces sortantes. Une interface sortante permet à l'objet de communiquer avec un client. Pour chaque interface sortante, l'objet connectable expose un point de connexion. Chaque interface sortante est implémentée par un client sur un objet appelé récepteur.

![Points de connexion](../atl/media/vc2zw31.gif "points de connexion")

Chaque point de connexion prend en charge la [IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint) interface. L’objet connectable expose ses points de connexion au client via le [IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer) interface.

## <a name="in-this-section"></a>Dans cette section

[ATL, classes de point de connexion](../atl/atl-connection-point-classes.md)<br/>
Décrit brièvement les classes ATL qui prennent en charge les points de connexion.

[Ajout de points de connexion à un objet](../atl/adding-connection-points-to-an-object.md)<br/>
Décrit les étapes à suivre pour ajouter des points de connexion à un objet.

[ATL, exemple de point de connexion](../atl/atl-connection-point-example.md)<br/>
Présente un exemple de déclaration de point de connexion.

## <a name="related-sections"></a>Rubriques connexes

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Propose des liens vers des rubriques conceptuelles traitant de la programmation à l'aide de la bibliothèque ATL (Active Template Library).

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)
