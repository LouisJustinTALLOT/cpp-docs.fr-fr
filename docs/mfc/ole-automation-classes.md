---
title: Classes Automation OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
ms.openlocfilehash: 08e33e1fce3f792e76e2eec4ecb59601c99d9822
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348716"
---
# <a name="ole-automation-classes"></a>Classes Automation OLE

Ces classes prennent en charge les clients automation (les applications qui contrôlent les autres applications). Serveurs Automation (les applications qui peuvent être contrôlées par d’autres applications) sont pris en charge par le biais [tables de dispatch](../mfc/reference/dispatch-maps.md).

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
Utilisé pour appeler des serveurs automation à partir de votre client automation. Lorsque vous ajoutez une classe, cette classe est utilisée pour créer des classes de type sécurisé pour les serveurs automation qui fournissent une bibliothèque de types.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Une exception résultant d’une erreur au cours de OLE automation. Exceptions de Automation sont générées par les serveurs automation et interceptées par les clients automation.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
