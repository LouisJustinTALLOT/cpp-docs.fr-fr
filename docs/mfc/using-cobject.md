---
title: Utilisation de CObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4e9e33ace99cded551abbb43bc9ada1c6c625eb
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693701"
---
# <a name="using-cobject"></a>Utilisation de CObject
[CObject](../mfc/reference/cobject-class.md) est la classe de base racine pour la plupart de la MFC Microsoft Foundation Class Library (). Le `CObject` classe contient de nombreuses fonctionnalités utiles que vous souhaitez incorporer dans vos propres objets, y compris la prise en charge de la sérialisation, les informations de classe d’exécution et sortie de diagnostic d’objet. Si vous dérivez votre classe de `CObject`, votre classe peut exploiter ces `CObject` fonctionnalités.  
  
## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi  
  
-   [Dérivez une classe de CObject](../mfc/deriving-a-class-from-cobject.md)  
  
-   [Ajouter la prise en charge des informations de classe d’exécution, la création dynamique et la sérialisation pour ma classe dérivée](../mfc/specifying-levels-of-functionality.md)  
  
-   [Accéder aux informations de classe d’exécution](../mfc/accessing-run-time-class-information.md)  
  
-   [Créer dynamiquement des objets](../mfc/dynamic-object-creation.md)  
  
-   [Vider les données de l’objet pour faciliter le diagnostic](/previous-versions/visualstudio/visual-studio-2010/sc15kz85\(v=vs.100\))  
  
-   Valider l’état interne de l’objet (consultez [MFC ASSERT_VALID et CObject::AssertValid](reference/diagnostic-services.md#assert_valid))  
  
-   [Que la classe se sérialiser vers le stockage persistant](../mfc/serialization-in-mfc.md)  
  
-   Afficher la liste des [CObject Forum aux Questions](../mfc/cobject-class-frequently-asked-questions.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../mfc/mfc-concepts.md)   
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)   
 [CRuntimeClass, Structure](../mfc/reference/cruntimeclass-structure.md)   
 [Fichiers](../mfc/files-in-mfc.md)   
 [Sérialisation](../mfc/serialization-in-mfc.md)

