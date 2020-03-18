---
title: Classes liées à OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: dfcc07b3fbd0c5badce8e397f4d52bc7d8d3028c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447609"
---
# <a name="ole-related-classes"></a>Classes liées à OLE

Ces classes fournissent un certain nombre de services différents, allant des exceptions à l’entrée et à la sortie de fichier.

[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)<br/>
Utilisé pour créer des éléments quand ils sont demandés à partir d’autres conteneurs. Cette classe sert de classe de base pour des types de fabriques plus spécifiques, y compris `COleTemplateServer`.

[COleMessageFilter](../mfc/reference/colemessagefilter-class.md)<br/>
Utilisé pour gérer l’accès concurrentiel avec les appels de procédure distante (LRPC) légers OLE.

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
Utilise l’interface de `IStream` COM pour fournir aux `CFile` l’accès aux fichiers composés. Cette classe (dérivée de `CFile`) permet à la sérialisation MFC d’utiliser le stockage structuré OLE.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Utilisé pour autoriser le déplacement, le redimensionnement et la réorientation des éléments sur place.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
