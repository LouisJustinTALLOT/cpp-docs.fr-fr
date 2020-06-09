---
title: Classes Automation OLE
ms.date: 11/04/2016
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
ms.openlocfilehash: 04cb93b8ce3699b579342d33c0dae77176878379
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625299"
---
# <a name="ole-automation-classes"></a>Classes Automation OLE

Ces classes prennent en charge les clients Automation (applications qui contrôlent d’autres applications). Les serveurs Automation (applications qui peuvent être contrôlées par d’autres applications) sont pris en charge via les [tables de dispatch](reference/dispatch-maps.md).

[COleDispatchDriver](reference/coledispatchdriver-class.md)<br/>
Utilisé pour appeler des serveurs Automation à partir de votre client Automation. Quand vous ajoutez une classe, cette classe permet de créer des classes de type sécurisé pour les serveurs Automation qui fournissent une bibliothèque de types.

[COleDispatchException](reference/coledispatchexception-class.md)<br/>
Exception résultant d’une erreur lors de l’automatisation d’OLE. Les exceptions Automation sont levées par les serveurs Automation et interceptées par les clients Automation.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
