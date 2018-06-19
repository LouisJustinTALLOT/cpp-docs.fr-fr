---
title: L’impression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7df782e3c30b9120fe7eb6728f1b622750d160f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348227"
---
# <a name="printing"></a>Impression
Microsoft Windows implémente un affichage est indépendant du périphérique. Dans MFC, cela signifie que les mêmes appels de dessin, dans le `OnDraw` fonction membre de votre classe d’affichage, sont chargés de dessin sur l’affichage et sur d’autres appareils, tels que des imprimantes. Pour l’aperçu avant impression, le périphérique cible est une sortie d’imprimante simulé à l’affichage.  
  
##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> Votre rôle dans l’impression par rapport à celui de l’infrastructure  
 Votre classe d’affichage présente les responsabilités suivantes :  
  
-   Informer l’infrastructure de nombre de pages contenues dans le document.  
  
-   Lorsque vous êtes invité à imprimer une page spécifique, tracer la partie du document.  
  
-   Allouer et libérer toutes les polices ou autres ressources de l’interface (GDI) de périphérique graphics nécessaires pour l’impression.  
  
-   Si nécessaire, envoyez les codes d’échappement nécessaires pour modifier le mode d’impression avant d’imprimer une page donnée, par exemple, pour modifier l’orientation de l’impression sur une base par page.  
  
 Responsabilités de l’infrastructure sont les suivantes :  
  
-   Afficher le **impression** boîte de dialogue.  
  
-   Créer un [CDC](../mfc/reference/cdc-class.md) objet pour l’imprimante.  
  
-   Appelez le [StartDoc](../mfc/reference/cdc-class.md#startdoc) et [EndDoc](../mfc/reference/cdc-class.md#enddoc) les fonctions membres de la `CDC` objet.  
  
-   Appeler le [StartPage](../mfc/reference/cdc-class.md#startpage) fonction membre de la `CDC` de l’objet, informer de la classe de vue quelle page doit être imprimée et appelez le [EndPage](../mfc/reference/cdc-class.md#endpage) fonction membre de la `CDC` objet.  
  
-   Appeler les fonctions substituables dans la vue au moment voulu.  
  
 Les articles suivants expliquent comment le framework prend en charge l’impression et Aperçu avant impression :  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Procédure d’impression par défaut](../mfc/how-default-printing-is-done.md)  
  
-   [Documents multipages](../mfc/multipage-documents.md)  
  
-   [En-têtes et pieds de page](../mfc/headers-and-footers.md)  
  
-   [Allocation de ressources GDI pour l’impression](../mfc/allocating-gdi-resources.md)  
  
-   [Aperçu avant impression](../mfc/print-preview-architecture.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Impression et aperçu avant impression](../mfc/printing-and-print-preview.md)

