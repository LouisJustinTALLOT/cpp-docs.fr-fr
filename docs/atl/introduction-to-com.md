---
title: Introduction à COM
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: 7631ba98b0e2cb00310400206b0b442ab7a23dd7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277428"
---
# <a name="introduction-to-com"></a>Introduction à COM

COM est « modèle objet » fondamentales sur les contrôles ActiveX et les OLE sont construits. COM permet à un objet d’exposer ses fonctionnalités à d’autres composants et d’héberger des applications. Il définit comment l’objet expose lui-même et comment cette exposition fonctionne sur les processus et les réseaux. COM définit également le cycle de vie de l’objet.

Fondamentaux de COM sont ces concepts :

- [Interfaces](../atl/interfaces-atl.md) — le mécanisme par lequel un objet expose ses fonctionnalités.

- [IUnknown](../atl/iunknown.md) : l’interface de base sur laquelle tous les autres sont basés. Il implémente le comptage de références et l’interface interrogation mécanismes en cours d’exécution via COM.

- [Comptage de références](../atl/reference-counting.md) — la technique par laquelle un objet (ou strictement, une interface) décide quand il n’est plus utilisé et est donc libre de supprimer elle-même.

- [QueryInterface](../atl/queryinterface.md) — la méthode utilisée pour interroger un objet d’une interface donnée.

- [Marshaling](../atl/marshaling.md) — le mécanisme qui permet aux objets à utiliser dans les limites du réseau, ce qui permet l’indépendance d’emplacement, de processus et de thread.

- [Agrégation](../atl/aggregation.md) — un moyen dans laquelle un objet peut faire utiliser d’une autre.

## <a name="see-also"></a>Voir aussi

[Introduction à COM et ATL](../atl/introduction-to-com-and-atl.md)<br/>
[COM (Component Object Model)](/windows/desktop/com/the-component-object-model)
