---
description: 'En savoir plus sur : philosophie générale de conception de classes'
title: Philosophie générale de conception des classes
ms.date: 11/04/2016
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 96069b5f30cbca8bb310de6b917fd65a280700b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193459"
---
# <a name="general-class-design-philosophy"></a>Philosophie générale de conception des classes

Microsoft Windows a été conçu longtemps avant que le langage C++ devienne populaire. Étant donné que des milliers d’applications utilisent l’interface de programmation d’applications (API) Windows en langage C, cette interface sera conservée dans un avenir prévisible. Toute interface Windows C++ doit donc être générée en plus de l’API de langage C procédurale. Cela garantit que les applications C++ pourront coexister avec les applications C.

Le bibliothèque MFC (Microsoft Foundation Class) est une interface orientée objet vers Windows qui répond aux objectifs de conception suivants :

- Réduction significative de l’effort d’écriture d’une application pour Windows.

- Vitesse d’exécution comparable à celle de l’API du langage C.

- Surcharge minimale de la taille du code.

- Possibilité d’appeler directement une fonction C Windows.

- Conversion plus facile des applications C existantes en C++.

- Possibilité de tirer parti de la base existante de l’expérience de programmation Windows en langage C.

- Utilisation plus facile de l’API Windows avec C++ qu’avec C.

- Il est plus facile d’utiliser des abstractions puissantes de fonctionnalités complexes, telles que les contrôles ActiveX, la prise en charge des bases de données, l’impression, les barres d’outils et les barres d’État.

- Véritable API Windows pour C++ qui utilise efficacement les fonctionnalités du langage C++.

Pour plus d’informations sur la conception de la bibliothèque MFC, consultez :

- [Infrastructure d’application](application-framework.md)

- [Relation avec l’API du langage C](relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
