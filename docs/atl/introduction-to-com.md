---
description: 'En savoir plus sur : présentation de COM'
title: Introduction à COM
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: 635bce8c1214dddfc258ae6d2d6c7e751f778e9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147665"
---
# <a name="introduction-to-com"></a>Introduction à COM

COM est le « modèle objet » fondamental sur lequel les contrôles ActiveX et OLE sont générés. COM permet à un objet d’exposer ses fonctionnalités à d’autres composants et d’héberger des applications. Il définit à la fois comment l’objet s’expose et comment cette exposition fonctionne sur les processus et sur les réseaux. COM définit également le cycle de vie de l’objet.

Les concepts fondamentaux de COM sont les suivants :

- [Interfaces](../atl/interfaces-atl.md) : mécanisme par lequel un objet expose ses fonctionnalités.

- [IUnknown](../atl/iunknown.md) : interface de base sur laquelle tous les autres sont basés. Il implémente le décompte de références et les mécanismes d’interrogation d’interface s’exécutant via COM.

- [Décompte de références](../atl/reference-counting.md) : technique par laquelle un objet (ou, strictement, une interface) décide quand il n’est plus utilisé et est donc libre de se supprimer lui-même.

- [QueryInterface](../atl/queryinterface.md) : méthode utilisée pour interroger un objet pour une interface donnée.

- [Marshaling](../atl/marshaling.md) : mécanisme qui permet aux objets d’être utilisés dans les limites du thread, du processus et du réseau, ce qui permet l’indépendance de l’emplacement.

- [Aggregation](../atl/aggregation.md) : méthode dans laquelle un objet peut utiliser un autre.

## <a name="see-also"></a>Voir aussi

[Introduction à COM et ATL](../atl/introduction-to-com-and-atl.md)<br/>
[COM (Component Object Model)](/windows/win32/com/the-component-object-model)
