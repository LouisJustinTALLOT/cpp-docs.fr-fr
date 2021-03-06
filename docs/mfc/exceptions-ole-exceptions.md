---
description: 'En savoir plus sur : exceptions : exceptions OLE'
title: 'Exceptions : exceptions OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: da2a92d23dc7c11735c75482febea60916af289f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290516"
---
# <a name="exceptions-ole-exceptions"></a>Exceptions : exceptions OLE

Les techniques et les fonctionnalités de gestion des exceptions dans OLE sont les mêmes que celles pour gérer d’autres exceptions. Pour plus d’informations sur la gestion des exceptions, consultez l’article [meilleures pratiques pour C++ moderne pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md).

Tous les objets exception sont dérivés de la classe de base abstraite `CException` . MFC fournit deux classes pour gérer les exceptions OLE :

- [COleException](reference/coleexception-class.md) Pour gérer les exceptions OLE générales.

- [COleDispatchException](reference/coledispatchexception-class.md) Pour générer et gérer les exceptions de dispatch OLE (Automation).

La différence entre ces deux classes est la quantité d’informations fournies et l’emplacement où elles sont utilisées. `COleException` a un membre de données public qui contient le code d’État OLE pour l’exception. `COleDispatchException` fournit plus d’informations, y compris les éléments suivants :

- Code d’erreur spécifique à l’application

- Description de l’erreur, telle que « disque plein »

- Contexte d’aide que votre application peut utiliser pour fournir des informations supplémentaires à l’utilisateur

- Nom du fichier d’aide de votre application

- Nom de l’application qui a généré l’exception

`COleDispatchException` fournit plus d’informations afin qu’il puisse être utilisé avec des produits tels que Microsoft Visual Basic. La description de l’erreur verbale peut être utilisée dans une boîte de message ou une autre notification. les informations d’aide peuvent être utilisées pour aider l’utilisateur à répondre aux conditions qui ont provoqué l’exception.

Deux fonctions globales correspondent aux deux classes d’exception OLE : [AfxThrowOleException](reference/exception-processing.md#afxthrowoleexception) et [AfxThrowOleDispatchException](reference/exception-processing.md#afxthrowoledispatchexception). Utilisez-les pour lever des exceptions OLE générales et des exceptions de dispatch OLE, respectivement.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
