---
title: Introduction à COM | Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0302727bba0155fe59ffa223f5e4e91ef3c122de
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754851"
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

[Introduction à COM et ATL](../atl/introduction-to-com-and-atl.md)   
[Le modèle d’objet composant](/windows/desktop/com/the-component-object-model)

