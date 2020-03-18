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
ms.openlocfilehash: 644a4930eb55636ba6e87b949ed610b725334661
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447685"
---
# <a name="ole-automation-classes"></a>Classes Automation OLE

Ces classes prennent en charge les clients Automation (applications qui contrôlent d’autres applications). Les serveurs Automation (applications qui peuvent être contrôlées par d’autres applications) sont pris en charge via les [tables de dispatch](../mfc/reference/dispatch-maps.md).

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
Utilisé pour appeler des serveurs Automation à partir de votre client Automation. Quand vous ajoutez une classe, cette classe permet de créer des classes de type sécurisé pour les serveurs Automation qui fournissent une bibliothèque de types.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Exception résultant d’une erreur lors de l’automatisation d’OLE. Les exceptions Automation sont levées par les serveurs Automation et interceptées par les clients Automation.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
