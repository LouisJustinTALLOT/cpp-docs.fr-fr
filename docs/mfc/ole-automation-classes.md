---
title: Classes Automation OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea35e51296b2fc528657c4dd9f9b9b76b84aae83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391512"
---
# <a name="ole-automation-classes"></a>Classes Automation OLE

Ces classes prennent en charge les clients automation (les applications qui contrôlent les autres applications). Serveurs Automation (les applications qui peuvent être contrôlées par d’autres applications) sont pris en charge par le biais [tables de dispatch](../mfc/reference/dispatch-maps.md).

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
Utilisé pour appeler des serveurs automation à partir de votre client automation. Lorsque vous ajoutez une classe, cette classe est utilisée pour créer des classes de type sécurisé pour les serveurs automation qui fournissent une bibliothèque de types.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Une exception résultant d’une erreur au cours de OLE automation. Exceptions de Automation sont générées par les serveurs automation et interceptées par les clients automation.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

