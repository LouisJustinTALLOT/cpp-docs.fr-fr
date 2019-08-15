---
title: Interfaces (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 2373351330982623ffa602fd81bec61d0bc257b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492136"
---
# <a name="interfaces-atl"></a>Interfaces (ATL)

Une interface est la façon dont un objet expose ses fonctionnalités au monde extérieur. Dans COM, une interface est un tableau de pointeurs (comme un C++ vtable) vers les fonctions implémentées par l’objet. Le tableau représente l’interface et les fonctions auxquelles il pointe sont les méthodes de cette interface. Un objet peut exposer autant d’interfaces qu’il le souhaite.

Chaque interface est basée sur l’interface COM fondamentale, [IUnknown](../atl/iunknown.md). Les méthodes de `IUnknown` permettent la navigation vers d’autres interfaces exposées par l’objet.

En outre, chaque interface reçoit un ID d’interface unique (IID). Cet unicité facilite la prise en charge du contrôle de version de l’interface. Une nouvelle version d’une interface est simplement une nouvelle interface, avec un nouvel IID.

> [!NOTE]
>  Les IID pour les interfaces COM et OLE standard sont prédéfinies.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Objets et interfaces COM](/windows/win32/com/com-objects-and-interfaces)
