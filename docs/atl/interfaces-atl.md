---
title: Interfaces (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 3f6e8978c01d6689118a3a004c48e75a40151490
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594738"
---
# <a name="interfaces-atl"></a>Interfaces (ATL)

Une interface est la méthode dans laquelle un objet expose ses fonctionnalités au monde extérieur. Dans COM, une interface est une table de pointeurs (comme un vtable C++) pour les fonctions implémentées par l’objet. La table représente l’interface, et les fonctions vers lequel il pointe sont les méthodes de cette interface. Un objet peut exposer autant d’interfaces qu’il le souhaite.

Chaque interface est basée sur l’interface COM fondamentale, [IUnknown](../atl/iunknown.md). Les méthodes de `IUnknown` autorisera la navigation vers d’autres interfaces exposées par l’objet.

En outre, chaque interface est dotée d’un unique ID d’interface (IID). Ce caractère unique facilite la charge du versioning. Une nouvelle version d’une interface est simplement une nouvelle interface, avec un nouveau IID.

> [!NOTE]
>  IID pour les interfaces COM et OLE standards sont prédéfinies.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Interfaces et des objets COM](/windows/desktop/com/com-objects-and-interfaces)

