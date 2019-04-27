---
title: Philosophie générale de conception des classes
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 4dfa11c73703f5f2d3d17f8278610d32178af679
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219617"
---
# <a name="general-class-design-philosophy"></a>Philosophie générale de conception des classes

Microsoft Windows a été conçue bien avant que le langage C++ sont devenus populaires. Étant donné que des milliers d’applications utilisent l’interface de programmation d’application (API) Windows du langage C, cette interface est conservée pour un avenir proche. N’importe quelle interface C++ Windows doit par conséquent être créé sur l’API du langage C procédural. Cela garantit que les applications C++ sera en mesure de coexister avec les applications C.

La bibliothèque Microsoft Foundation Class est une interface orientée objet pour Windows qui répond aux objectifs de conception suivantes :

- Réduction significative de l’effort nécessaire pour écrire une application pour Windows.

- Vitesse d’exécution comparable à celle de l’API de langage C.

- Surcharge de la taille minimum de code.

- Possibilité d’appeler directement de n’importe quelle fonction C de Windows.

- Faciliter la conversion des applications C existantes à C++.

- Possibilité de tirer parti de la base existante de Windows en langage C expérience de programmation.

- Une utilisation plus simple de l’API Windows avec C++ qu’avec C.

- Plus facile à utiliser encore des abstractions puissantes de compliquée des fonctionnalités telles que les contrôles ActiveX, prise en charge de la base de données, l’impression, barres d’outils et barres d’état.

- API Windows True pour C++ qui utilise efficacement les fonctionnalités du langage C++.

Pour plus d’informations sur la conception de la bibliothèque MFC, consultez :

- [L’infrastructure d’Application](../mfc/application-framework.md)

- [Relation avec l’API du langage C](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
