---
description: 'En savoir plus sur : conteneurs : États de Client-Item'
title: "Conteneurs : états d'élément client"
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 2f6560b5694bcd7a55b7547593d9ba2dc9a93389
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310458"
---
# <a name="containers-client-item-states"></a>Conteneurs : états d'élément client

Cet article explique les différents états par lesquels passe un élément client pendant son cycle de vie.

Un élément client passe par plusieurs états lorsqu'il est créé, activé, modifié et enregistré. Chaque fois que l’état de l’élément change, le Framework appelle [COleClientItem :: OnChange](reference/coleclientitem-class.md#onchange) avec la notification **OLE_CHANGED_STATE** . Le deuxième paramètre est une valeur de l' `COleClientItem::ItemState` énumération. Les valeurs possibles sont les suivantes :

- *COleClientItem::emptyState*

- *COleClientItem::loadedState*

- *COleClientItem::openState*

- *COleClientItem::activeState*

- *COleClientItem::activeUIState*

Dans l'état vide, un élément client n'est pas encore complètement un élément. De la mémoire lui a été allouée, mais elle n'a pas encore été initialisée avec les données de l'élément OLE. Il s’agit de l’État dans lequel se trouve un élément client lorsqu’il a été créé via un appel à **`new`** mais n’a pas encore subi la deuxième étape de la création classique en deux étapes.

Dans la deuxième étape, effectuée par le biais d’un appel à `COleClientItem::CreateFromFile` ou d’une autre `CreateFrom` fonction *xxxx* , l’élément est entièrement créé. Les données OLE (d'un fichier ou d'une autre source, telle que le Presse-papiers) ont été associées à l'objet dérivé de `COleClientItem`. Maintenant l'élément se trouve dans l'état chargé.

Lorsqu'un élément a été ouvert dans la fenêtre du serveur au lieu d'être ouvert sur place dans le document du conteneur, il se trouve dans l'état ouvert (ou entièrement ouvert). Dans cet état, une hachure croisée est généralement dessinée sur la représentation de l'élément dans la fenêtre du conteneur pour indiquer que l'élément est actif ailleurs.

Lorsqu'un élément a été activé sur place, il ne passe généralement que brièvement par l'état actif. Il passe ensuite à l’état actif de l’interface utilisateur, dans lequel le serveur a fusionné ses menus, barres d’outils et autres composants d’interface utilisateur avec ceux du conteneur. La présence de ces composants d'interface utilisateur fait la distinction entre l'état actif de l'interface utilisateur et l'état actif. Sinon, l'état actif s'apparente à l'état actif de l'interface utilisateur. Si le serveur prend en charge l'annulation, il doit conserver les informations d'état d'annulation de l'élément OLE jusqu'à ce que ce dernier atteigne l'état chargé ou ouvert.

## <a name="see-also"></a>Voir aussi

[Containers](containers.md)<br/>
[Activation](activation-cpp.md)<br/>
[Conteneurs : notifications de Client-Item](containers-client-item-notifications.md)<br/>
[Trackers](trackers.md)<br/>
[CRectTracker (classe)](reference/crecttracker-class.md)
