---
title: Interfaces (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 56d5a010bc28257dce181ee33e0ddf74655ccd3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319385"
---
# <a name="interfaces-atl"></a>Interfaces (ATL)

Une interface est la façon dont un objet expose sa fonctionnalité au monde extérieur. Dans COM, une interface est un tableau de pointeurs (comme un Vtable C) aux fonctions implémentées par l’objet. Le tableau représente l’interface, et les fonctions auxquelles il pointe sont les méthodes de cette interface. Un objet peut exposer autant d’interfaces qu’il le souhaite.

Chaque interface est basée sur l’interface COM fondamentale, [IUnknown](../atl/iunknown.md). Les méthodes `IUnknown` de permettre la navigation à d’autres interfaces exposées par l’objet.

En outre, chaque interface est donnée un ID interface unique (IID). Cette singularité facilite la version interface. Une nouvelle version d’une interface est simplement une nouvelle interface, avec un nouvel IID.

> [!NOTE]
> Les DIE pour les interfaces STANDARD COM et OLE sont prédéfinis.

## <a name="see-also"></a>Voir aussi

[Introduction à COM](../atl/introduction-to-com.md)<br/>
[Objets et Interfaces COM](/windows/win32/com/com-objects-and-interfaces)
