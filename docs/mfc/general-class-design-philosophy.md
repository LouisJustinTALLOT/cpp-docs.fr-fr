---
title: Philosophie générale de conception des classes
ms.date: 11/04/2016
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 34a173802e3fa43615c05da4ce747592f851228f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441185"
---
# <a name="general-class-design-philosophy"></a>Philosophie générale de conception des classes

Microsoft Windows a été conçu longtemps avant C++ que la langue ne soit devenue populaire. Étant donné que des milliers d’applications utilisent l’interface de programmation d’applications (API) Windows en langage C, cette interface sera conservée dans un avenir prévisible. Toute C++ interface Windows doit donc être générée en plus de l’API de langage C. Cela garantit que C++ les applications seront en mesure de coexister avec les applications C.

Le bibliothèque MFC (Microsoft Foundation Class) est une interface orientée objet vers Windows qui répond aux objectifs de conception suivants :

- Réduction significative de l’effort d’écriture d’une application pour Windows.

- Vitesse d’exécution comparable à celle de l’API du langage C.

- Surcharge minimale de la taille du code.

- Possibilité d’appeler directement une fonction C Windows.

- Conversion plus facile des applications C existantes C++en.

- Possibilité de tirer parti de la base existante de l’expérience de programmation Windows en langage C.

- Utilisation plus facile de l’API Windows C++ avec C.

- Il est plus facile d’utiliser des abstractions puissantes de fonctionnalités complexes, telles que les contrôles ActiveX, la prise en charge des bases de données, l’impression, les barres d’outils et les barres d’État.

- Véritable API Windows pour C++ qui utilise C++ efficacement les fonctionnalités de langage.

Pour plus d’informations sur la conception de la bibliothèque MFC, consultez :

- [Infrastructure d’application](../mfc/application-framework.md)

- [Relation avec l’API du langage C](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
