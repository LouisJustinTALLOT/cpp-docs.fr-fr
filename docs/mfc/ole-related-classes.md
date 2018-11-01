---
title: Classes liées à OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: 2c3aa5ea4e720b14c5fdc4cb3285cd812eb550e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584650"
---
# <a name="ole-related-classes"></a>Classes liées à OLE

Ces classes fournissent un nombre de services différents, allant des exceptions dans le fichier d’entrée et de sortie.

[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)<br/>
Utilisé pour créer des éléments de demande à partir d’autres conteneurs. Cette classe sert de classe de base pour les types de fabriques, y compris les plus spécifiques `COleTemplateServer`.

[Intermédiaire de COleMessageFilter](../mfc/reference/colemessagefilter-class.md)<br/>
Utilisé pour gérer l’accès concurrentiel avec OLE légère à distance procédure appels (LRPC).

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
Utilise le modèle COM `IStream` interface pour fournir `CFile` accès aux fichiers composés. Cette classe (dérivée de `CFile`) permet la sérialisation MFC utiliser un stockage structuré OLE.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Utilisé pour permettre le déplacement, redimensionnement et réorientation des éléments de la place.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

