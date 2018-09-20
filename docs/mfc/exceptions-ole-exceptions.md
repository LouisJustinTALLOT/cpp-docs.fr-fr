---
title: 'Exceptions : Exceptions OLE | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6013caa79e21a305ba5ff8ad6266e960bb21504a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395243"
---
# <a name="exceptions-ole-exceptions"></a>Exceptions : exceptions OLE

Les techniques et les fonctionnalités de gestion des exceptions dans OLE sont les mêmes que celles pour gérer les autres exceptions. Pour plus d’informations sur la gestion des exceptions, consultez l’article [gestion des exceptions C++](../cpp/cpp-exception-handling.md).

Tous les objets d’exception sont dérivés de la classe de base abstraite `CException`. MFC fournit deux classes pour la gestion des exceptions OLE :

- [COleException](../mfc/reference/coleexception-class.md) pour la gestion des exceptions générales OLE.

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) pour générer et gérer OLE distribuer les exceptions (automation).

La différence entre ces deux classes est la quantité d’informations qu’ils fournissent et où ils sont utilisés. `COleException` possède un membre de données publiques qui contient le code d’état OLE pour l’exception. `COleDispatchException` fournit plus d’informations, notamment les suivantes :

- Un code d’erreur spécifique à l’application

- Une description de l’erreur, telles que « Disque plein »

- Un contexte d’aide que votre application peut utiliser pour fournir des informations supplémentaires pour l’utilisateur

- Le nom du fichier d’aide de votre application

- Le nom de l’application qui a généré l’exception

`COleDispatchException` Fournit des informations supplémentaires afin qu’il peut être utilisé avec des produits tels que Microsoft Visual Basic. La description d’erreur peut être utilisée dans une boîte de message ou toute autre notification ; les informations d’aide peuvent être utilisées pour aider l’utilisateur à répondre aux conditions ayant provoqué l’exception.

Deux fonctions globales correspondent aux deux classes d’exception OLE : [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception) et [AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Utilisez-les pour lever des exceptions générales OLE et des exceptions de dispatch OLE, respectivement.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

