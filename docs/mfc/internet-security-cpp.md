---
description: 'En savoir plus sur : sécurité Internet (C++)'
title: Sécurité Internet (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
ms.openlocfilehash: 870695abc89ba022a333829ec974d2f1e9147a53
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335847"
---
# <a name="internet-security-c"></a>Sécurité Internet (C++)

La sécurité du code est un problème majeur pour les développeurs et les utilisateurs d’applications Internet. Il existe des risques : du code malveillant, du code qui a été falsifié et du code provenant de sites ou d’auteurs inconnus.

Il existe deux approches de base en matière de sécurité lors du développement pour Internet. La première est appelée « sandboxing ». Dans cette approche, une application est limitée à un ensemble particulier d’API et exclue de celles potentiellement dangereuses telles que les e/s de fichier où un programme peut détruire des données sur l’ordinateur d’un utilisateur. La seconde est implémentée à l’aide de signatures numériques. Cette approche est appelée « shrinkwrap » pour Internet. Le code est vérifié et signé à l’aide de la technologie de clé privée/clé publique. Avant l’exécution du code, sa signature numérique est vérifiée pour s’assurer que le code provient d’une source authentifiée connue et que le code n’a pas été modifié depuis qu’il a été signé.

Dans le premier cas, vous faites confiance au fait que l’application n’est pas lésée et que vous faites confiance à l’origine de l’application. Dans le second, les signatures numériques sont utilisées pour vérifier l’authenticité. La signature numérique est une norme de l’industrie utilisée pour identifier et fournir des détails sur l’éditeur du code. Sa technologie est basée sur les normes, notamment RSA et X. 509. En général, les navigateurs permettent aux utilisateurs de choisir s’ils souhaitent télécharger et exécuter le code d’origine inconnue.

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](mfc-internet-programming-tasks.md)<br/>
[Concepts de base de la programmation Internet MFC](mfc-internet-programming-basics.md)
