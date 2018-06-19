---
title: Classes liées à OLE | Documents Microsoft
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
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: baa4ec3de21ce91e0d8723ad0e4debb39a26b3cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348513"
---
# <a name="ole-related-classes"></a>Classes liées à OLE
Ces classes fournissent un nombre de services différents, allant des exceptions dans le fichier d’entrée et de sortie.  
  
 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)  
 Permet de créer des éléments lorsqu’il est demandé à partir d’autres conteneurs. Cette classe sert de classe de base pour les types plus spécifiques des fabriques, y compris `COleTemplateServer`.  
  
 [Intermédiaire de COleMessageFilter](../mfc/reference/colemessagefilter-class.md)  
 Utilisé pour gérer l’accès concurrentiel avec OLE Lightweight distant procédure appelle (LRPC).  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 Utilise le modèle COM `IStream` interface afin de fournir `CFile` accès aux fichiers composés. Cette classe (dérivée de `CFile`) permet la sérialisation MFC utiliser le stockage structuré OLE.  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 Utilisée pour autoriser le déplacement, redimensionnement et réorientation d’éléments de la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

