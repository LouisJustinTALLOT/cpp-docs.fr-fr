---
title: MFC COM | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC COM (MFC)
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8257631e46a1ebcf5c882d9f87c628c04ccc84f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347771"
---
# <a name="mfc-com"></a>MFC COM
Un sous-ensemble de MFC est conçu pour prendre en charge COM, alors que la plupart de la bibliothèque ATL (Active Template) est conçu pour la programmation COM. Cette section décrit la prise en charge de MFC pour COM.  
  
 Les technologies Active (telles que ActiveX des contrôles, relation contenant-contenu de document actif, OLE et ainsi de suite) utilisent le modèle COM (Component Object) pour activer les composants logiciels d’interagir avec eux dans un environnement réseau, quel que soit le langage avec lequel ils ont été créé. Technologies actives peuvent être utilisés pour créer des applications qui s’exécutent sur le bureau ou sur Internet. Pour plus d’informations, consultez [Introduction à COM](../atl/introduction-to-com.md) ou [le modèle](http://msdn.microsoft.com/library/windows/desktop/ms694363).  
  
 Les technologies Active incluent des technologies de client et le serveur, notamment les suivantes :  
  
-   [Relation contenant-contenu de document actif](../mfc/active-document-containment.md), pris en charge dans les versions 4.2 et versions ultérieures, permet aux utilisateurs d’afficher [documents actifs](../mfc/active-documents.md) (tels que les fichiers Microsoft Excel ou Word) et activer l’interface native du document application dans la zone cliente d’une [conteneur de documents actifs](../mfc/active-document-containers.md) tels qu’un classeur Microsoft Office ou Microsoft Internet Explorer. Les conteneurs agissent comme des clients, tandis que les documents sont fournis par [serveurs de documents actifs](../mfc/active-document-servers.md). Pour plus d’informations sur l’utilisation de documents actifs dans les applications Internet, consultez : [Documents actifs sur Internet](../mfc/active-documents-on-the-internet.md).  
  
-   Contrôles ActiveX sont des objets interactifs qui peuvent être utilisés dans des conteneurs, tel qu’un site Web. Pour plus d’informations sur les contrôles ActiveX, consultez :  
  
    -   [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
    -   [Contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md)  
  
    -   [Vue d’ensemble : Internet](../mfc/mfc-internet-programming-basics.md)  
  
    -   [Mise à niveau d’un contrôle ActiveX à utiliser sur Internet](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [Débogage d’un contrôle ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)  
  
-   Les scripts actifs contrôlent le comportement intégré d’un ou plusieurs contrôles ActiveX à partir d’un navigateur ou un serveur. Pour plus d’informations sur les scripts actifs, consultez [technologie Active sur Internet](../mfc/active-technology-on-the-internet.md).  
  
-   [Automation](../mfc/automation.md) (anciennement appelé OLE Automation) permet à une application de manipuler des objets implémentés dans une autre application, ou de « exposer » des objets pour qu’ils puissent être manipulés.  
  
     L’objet automatisé peut être local ou distant (sur un autre ordinateur accessible via un réseau). Automation est disponible pour les objets OLE et COM.  
  
-   Cette section fournit également des informations sur la façon d’écrire des composants COM à l’aide de MFC, par exemple, dans [Points de connexion](../mfc/connection-points.md).  
  
 Pour en savoir plus sur ce qui est toujours appelé OLE et ce que l'on appelle maintenant la technologie active, consultez les rubriques sur [OLE](../mfc/ole-in-mfc.md).  
  
 En outre, consultez l’article de la Base de connaissances Q248019 : comment faire : empêcher serveur occupé boîte de dialogue zone à partir d’apparaissant pendant une longue COM opération.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Documents actifs (contenance)](../mfc/active-document-containment.md)  
  
 [Automation](../mfc/automation.md)  
  
 [Points de connexion](../mfc/connection-points.md)  
  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../mfc/mfc-concepts.md)

