---
title: Glisser -déplacer (OLE) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc23c7695bf5afa22734c382ddc72e8418ff74c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344331"
---
# <a name="drag-and-drop-ole"></a>Glisser-déposer (OLE)
La fonctionnalité glisser-déplacer de l’OLE est essentiellement un raccourci pour copier et coller des données. Lorsque vous utilisez le Presse-papiers pour copier et coller des données, un certain nombre d'étapes sont nécessaires. Vous sélectionnez les données, cliquez sur **couper** ou **copie** à partir de la **modifier** menu, déplacer vers le fichier de destination, la fenêtre ou l’application, placez le curseur dans l’emplacement souhaité, puis cliquez sur **Coller** à partir de la **modifier** menu.  
  
 La fonction Glisser-déposer OLE est différente du mécanisme Glisser-déposer du gestionnaire de fichiers, qui ne peut gérer que les noms de fichiers et est conçu spécifiquement pour transmettre les noms de fichiers aux applications. Cette fonction est beaucoup plus générale. Vous pouvez ainsi faire glisser et déposer toutes les données qui peuvent être placées dans le Presse-papiers.  
  
 Lorsque vous utilisez la fonction Glisser-déposer OLE, vous supprimez deux étapes du processus. Sélectionnez les données de la fenêtre source (la "source de déplacement"), faites-la glisser vers la destination souhaitée (la "cible de dépôt"), puis supprimez-la en relâchant le bouton de la souris. L'opération permet de se passer des menus ; elle est plus rapide que la séquence copier/coller. Le seul impératif est que la source de déplacement et la cible de dépôt doivent être ouvertes et au moins partiellement visibles à l’écran.  
  
 La fonction Glisser-déposer OLE vous permet de transférer des données d’un emplacement à un autre au sein d’un document, entre des documents, ou entre des applications. Elle peut être implémentée dans un conteneur ou une application serveur, et toute application peut être une source déroulante, une cible de dépôt, ou les deux. Si une application prend à la fois en charge la source de dépôt et la cible de dépôt, la fonction Glisser-déposer est activée entre les fenêtres enfants, ou dans une fenêtre. Cette fonctionnalité facilite l’utilisation de votre application.  
  
 Si vous souhaitez uniquement utiliser les fonctions glisser-déplacer OLE, consultez [glisser -déplacer : personnalisation](../mfc/drag-and-drop-customizing.md). Vous pouvez utiliser les techniques expliquées dans cet article pour créer des sources de dépôt d’applications autres que OLE. L’article [glisser -déplacer : implémentation d’une cible de dépôt](../mfc/drag-and-drop-implementing-a-drop-target.md) décrit comment implémenter la prise en charge de la cible de dépôt pour les applications OLE et non OLE. Il sera également utile d’examiner les exemples OLE MFC [OCLIENT](../visual-cpp-samples.md) et [HIERSVR](../visual-cpp-samples.md).  
  
 Si vous n’avez pas lu la [des objets de données et Sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md) famille d’articles, vous souhaiterez faire maintenant. Ces articles décrivent les aspects fondamentaux du transfert de données, ainsi que leur implémentation dans vos applications.  
  
 Pour plus d’informations sur la fonction Glisser-déposer, consultez les rubriques suivantes :  
  
-   [Glisser-déposer : implémentation d’une source de dépôt](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Glisser-déposer : implémentation d’une cible de dépôt](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Glisser-déposer : personnalisation](../mfc/drag-and-drop-customizing.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OLE](../mfc/ole-in-mfc.md)   
 [Objets de données et sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md)

