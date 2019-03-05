---
title: Utilisation de CObject
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
ms.openlocfilehash: 15b5bebb8e75d24b769cd29971d08b3fbf92fcf8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302128"
---
# <a name="using-cobject"></a>Utilisation de CObject

[CObject](../mfc/reference/cobject-class.md) est la classe de base racine pour la plupart de la MFC Microsoft Foundation Class Library (). Le `CObject` classe contient de nombreuses fonctionnalités utiles que vous souhaitez incorporer dans vos propres objets, y compris la prise en charge de la sérialisation, les informations de classe d’exécution et sortie de diagnostic d’objet. Si vous dérivez votre classe de `CObject`, votre classe peut exploiter ces `CObject` fonctionnalités.

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

- [Dérivez une classe de CObject](../mfc/deriving-a-class-from-cobject.md)

- [Ajouter la prise en charge des informations de classe d’exécution, la création dynamique et la sérialisation pour ma classe dérivée](../mfc/specifying-levels-of-functionality.md)

- [Accéder aux informations de classe d’exécution](../mfc/accessing-run-time-class-information.md)

- [Créer dynamiquement des objets](../mfc/dynamic-object-creation.md)

- [Vider les données de l’objet pour faciliter le diagnostic](/previous-versions/visualstudio/visual-studio-2010/sc15kz85)

- Valider l’état interne de l’objet (consultez [MFC ASSERT_VALID et CObject::AssertValid](reference/diagnostic-services.md#assert_valid))

- [Que la classe se sérialiser vers le stockage persistant](../mfc/serialization-in-mfc.md)

- Afficher la liste des [CObject Forum aux Questions](../mfc/cobject-class-frequently-asked-questions.md)

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)<br/>
[Rubriques MFC générales](../mfc/general-mfc-topics.md)<br/>
[CRuntimeClass, structure](../mfc/reference/cruntimeclass-structure.md)<br/>
[Fichiers](../mfc/files-in-mfc.md)<br/>
[Sérialisation](../mfc/serialization-in-mfc.md)
