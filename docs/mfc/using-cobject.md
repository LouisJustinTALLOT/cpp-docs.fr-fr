---
description: 'En savoir plus sur : utilisation de CObject'
title: Utilisation de CObject
ms.date: 11/04/2016
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
ms.openlocfilehash: 203e2a498f787f23de21db4469e5cdd7c5543761
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271640"
---
# <a name="using-cobject"></a>Utilisation de CObject

[CObject](../mfc/reference/cobject-class.md) est la classe de base racine pour la plupart des bibliothèque MFC (Microsoft Foundation Class) (MFC). La `CObject` classe contient de nombreuses fonctionnalités utiles que vous pouvez incorporer dans vos propres objets de programme, notamment la prise en charge de la sérialisation, les informations de classe au moment de l’exécution et la sortie de diagnostic d’objet. Si vous dérivez votre classe de `CObject` , votre classe peut exploiter ces `CObject` fonctionnalités.

## <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

- [Dériver une classe de CObject](../mfc/deriving-a-class-from-cobject.md)

- [Ajouter la prise en charge des informations de classe au moment de l’exécution, la création dynamique et la sérialisation à ma classe dérivée](../mfc/specifying-levels-of-functionality.md)

- [Accéder aux informations de classe d’exécution](../mfc/accessing-run-time-class-information.md)

- [Créer des objets dynamiquement](../mfc/dynamic-object-creation.md)

- [Vider les données de l’objet à des fins de diagnostic](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))

- Valider l’état interne de l’objet (voir [MFC ASSERT_VALID et CObject :: AssertValid](reference/diagnostic-services.md#assert_valid))

- [Faire en sorte que la classe se sérialise lui-même vers le stockage persistant](../mfc/serialization-in-mfc.md)

- Voir la liste des [questions fréquemment posées sur CObject](../mfc/cobject-class-frequently-asked-questions.md)

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)<br/>
[Rubriques générales sur MFC](../mfc/general-mfc-topics.md)<br/>
[Structure CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)<br/>
[Fichiers](../mfc/files-in-mfc.md)<br/>
[Sérialisation](../mfc/serialization-in-mfc.md)
