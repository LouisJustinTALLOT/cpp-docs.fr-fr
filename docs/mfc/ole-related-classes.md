---
title: Classes liées à OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: 6f6db6ce133b440a5ed86e7c1642396888744540
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621032"
---
# <a name="ole-related-classes"></a>Classes liées à OLE

Ces classes fournissent un certain nombre de services différents, allant des exceptions à l’entrée et à la sortie de fichier.

[COleObjectFactory](reference/coleobjectfactory-class.md)<br/>
Utilisé pour créer des éléments quand ils sont demandés à partir d’autres conteneurs. Cette classe sert de classe de base pour des types de fabriques plus spécifiques, y compris `COleTemplateServer` .

[COleMessageFilter](reference/colemessagefilter-class.md)<br/>
Utilisé pour gérer l’accès concurrentiel avec les appels de procédure distante (LRPC) légers OLE.

[COleStreamFile](reference/colestreamfile-class.md)<br/>
Utilise l' `IStream` interface com pour fournir l' `CFile` accès aux fichiers composés. Cette classe (dérivée de `CFile` ) permet à la SÉRIALISATION MFC d’utiliser le stockage structuré OLE.

[CRectTracker](reference/crecttracker-class.md)<br/>
Utilisé pour autoriser le déplacement, le redimensionnement et la réorientation des éléments sur place.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
