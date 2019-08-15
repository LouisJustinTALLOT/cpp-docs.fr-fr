---
title: Introduction à COM
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: e29f761e0380357bc999af82cc4bde8bfbaf4d6e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492352"
---
# <a name="introduction-to-com"></a>Introduction à COM

COM est le «modèle objet» fondamental sur lequel les contrôles ActiveX et OLE sont générés. COM permet à un objet d’exposer ses fonctionnalités à d’autres composants et d’héberger des applications. Il définit à la fois comment l’objet s’expose et comment cette exposition fonctionne sur les processus et sur les réseaux. COM définit également le cycle de vie de l’objet.

Les concepts fondamentaux de COM sont les suivants:

- [Interfaces](../atl/interfaces-atl.md) : mécanisme par lequel un objet expose ses fonctionnalités.

- [IUnknown](../atl/iunknown.md) : interface de base sur laquelle tous les autres sont basés. Il implémente le décompte de références et les mécanismes d’interrogation d’interface s’exécutant via COM.

- [Décompte de références](../atl/reference-counting.md) : technique par laquelle un objet (ou, strictement, une interface) décide quand il n’est plus utilisé et est donc libre de se supprimer lui-même.

- [QueryInterface](../atl/queryinterface.md) : méthode utilisée pour interroger un objet pour une interface donnée.

- [Marshaling](../atl/marshaling.md) : mécanisme qui permet aux objets d’être utilisés dans les limites du thread, du processus et du réseau, ce qui permet l’indépendance de l’emplacement.

- [Aggregation](../atl/aggregation.md) : méthode dans laquelle un objet peut utiliser un autre.

## <a name="see-also"></a>Voir aussi

[Introduction à COM et ATL](../atl/introduction-to-com-and-atl.md)<br/>
[COM (Component Object Model)](/windows/win32/com/the-component-object-model)
