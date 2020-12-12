---
description: 'En savoir plus sur : interfaces (ATL)'
title: Interfaces (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: d68f482d05ff828631f5f9f27085f24af188d643
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147691"
---
# <a name="interfaces-atl"></a>Interfaces (ATL)

Une interface est la façon dont un objet expose ses fonctionnalités au monde extérieur. Dans COM, une interface est un tableau de pointeurs (comme une vtable C++) vers les fonctions implémentées par l’objet. Le tableau représente l’interface et les fonctions auxquelles il pointe sont les méthodes de cette interface. Un objet peut exposer autant d’interfaces qu’il le souhaite.

Chaque interface est basée sur l’interface COM fondamentale, [IUnknown](../atl/iunknown.md). Les méthodes de `IUnknown` permettent la navigation vers d’autres interfaces exposées par l’objet.

En outre, chaque interface reçoit un ID d’interface unique (IID). Cet unicité facilite la prise en charge du contrôle de version de l’interface. Une nouvelle version d’une interface est simplement une nouvelle interface, avec un nouvel IID.

> [!NOTE]
> Les IID pour les interfaces COM et OLE standard sont prédéfinies.

## <a name="see-also"></a>Voir aussi

[Introduction à COM](../atl/introduction-to-com.md)<br/>
[Objets et interfaces COM](/windows/win32/com/com-objects-and-interfaces)
