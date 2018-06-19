---
title: Philosophie générale de conception de classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b2d0915c4b2940e93b781e7a56e2640c64a7f20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344361"
---
# <a name="general-class-design-philosophy"></a>Philosophie générale de conception des classes
Microsoft Windows a été conçu bien avant que le langage C++ célèbres. Étant donné que des milliers d’applications utilisent l’interface de programmation d’application (API) en langage C Windows, cette interface est conservée pour un futur prévisible. N’importe quelle interface Windows C++ doit par conséquent être créé sur l’API du langage C procédurale. Cela garantit que les applications C++ sera en mesure de coexister avec les applications C.  
  
 La bibliothèque Microsoft Foundation Class est une interface orientée objet pour Windows qui répond aux objectifs de conception suivantes :  
  
-   Réduction significative de l’effort d’écrire une application pour Windows.  
  
-   Vitesse d’exécution comparable à celle de l’API en langage C.  
  
-   Surcharge de la taille minimum de code.  
  
-   Possibilité d’appeler directement de n’importe quelle fonction C de Windows.  
  
-   Faciliter la conversion d’applications C existantes pour C++.  
  
-   Possibilité de tirer parti de la base existante de Windows en langage C expérience de programmation.  
  
-   Plus facile d’utiliser de l’API Windows avec C++ avec C.  
  
-   Plus facile à utiliser mais puissantes abstractions de compliqué des fonctionnalités telles que les contrôles ActiveX, prise en charge de la base de données, l’impression, barres d’outils et barres d’état.  
  
-   API Windows True pour C++ qui utilisent efficacement les fonctionnalités du langage C++.  
  
 Pour plus d’informations sur la conception de la bibliothèque MFC, consultez :  
  
-   [L’infrastructure d’Application](../mfc/application-framework.md)  
  
-   [Relation avec l’API du langage C](../mfc/relationship-to-the-c-language-api.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

