---
title: Activation (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
ms.openlocfilehash: 47640a59180348bd3513013b65029a775545e211
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619184"
---
# <a name="activation-c"></a>Activation (C++)

Cet article explique le rôle de l'activation dans la modification visuelle des éléments OLE. Une fois qu'un utilisateur a incorporé un élément OLE dans un document conteneur, il peut être amené à l'utiliser. Pour ce faire, il double-clique sur l'élément, ce qui l'active. L'activité la plus fréquente pour l'activation est la modification. De nombreux éléments OLE actuels, une fois activés pour la modification, provoquent la modification des menus et barres d'outils de la fenêtre frame actuelle pour refléter ceux appartenant à l'application serveur qui a créé l'élément. Ce comportement, appelé activation sur place, permet à l'utilisateur de modifier un élément incorporé dans un document composite sans quitter la fenêtre du document conteneur.

Il est également possible de modifier des éléments OLE incorporés dans une fenêtre distincte. Cela se produit si l'application conteneur ou serveur ne prend pas en charge l'activation sur place. Dans ce cas, lorsque l'utilisateur double-clique sur un élément incorporé, l'application serveur est lancée dans une fenêtre distincte et l'élément incorporé apparaît comme son propre document. L'utilisateur modifie l'élément dans cette fenêtre. Une fois la modification terminée, l'utilisateur ferme l'application serveur et retourne à l'application conteneur.

En guise d’alternative, l’utilisateur peut choisir « ouvrir la modification » à l’aide de la commande ** \<object> ouvrir** du menu **Edition** . Cela ouvre l'objet dans une fenêtre distincte.

> [!NOTE]
> La modification des éléments incorporés dans une fenêtre distincte était un comportement standard d'OLE version 1, et certaines applications OLE ne peuvent prendre en charge que ce style de modification.

L'activation sur place utilise une approche centrée sur le document pour documenter la création. L'utilisateur peut traiter un document composite comme une entité unique et l'utiliser sans basculer entre les applications. Toutefois, l'activation sur place n'est utilisée que pour les éléments incorporés, pas pour les éléments liés qui doivent être modifiés dans une fenêtre distincte. Cela est dû au fait qu'un élément lié est en réalité stocké dans un emplacement différent. La modification d'un élément lié a lieu dans le contexte réel des données, c'est-à-dire, l'emplacement de stockage des données. La modification d'un élément lié dans une fenêtre distincte rappelle à l'utilisateur que les données appartiennent à un autre document.

MFC ne prend pas en charge l'activation sur place imbriquée. Si vous créez une application conteneur ou serveur et si ce conteneur ou serveur est incorporé dans un autre conteneur et activé sur place, il ne peut pas activer sur place les objets qui y sont incorporés.

Ce qui arrive à un élément incorporé lorsque l'utilisateur double-clique dessus dépend des verbes définis pour l'élément. Pour plus d’informations, consultez [activation : verbes](activation-verbs.md).

## <a name="see-also"></a>Voir aussi

[OLE](ole-in-mfc.md)<br/>
[Containers](containers.md)<br/>
[Serveurs](servers.md)
