---
title: Sécurité Internet (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b61df9a17903f50ea922edf9c29eee926063254
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055409"
---
# <a name="internet-security-c"></a>Sécurité Internet (C++)

Sécurité du code est un problème majeur pour les développeurs et les utilisateurs d’applications Internet. Il existe des risques : code malveillant, le code qui a été falsifié et code à partir de sites ou inconnus auteurs.

Il existe deux approches de base concernant la sécurité lors du développement pour Internet. La première est appelée « sandbox ». Dans cette approche, une application est limitée à un ensemble particulier d’API et exclue parmi ceux qui sont potentiellement dangereuses telles que les e/s de fichier dans lequel un programme peut détruire des données sur l’ordinateur d’un utilisateur. La seconde est implémentée à l’aide de signatures numériques. Cette approche est appelée « shrinkwrap » pour Internet. Code est vérifié et signé à l’aide de la technologie de clés publique/privée. Avant l’exécution du code, sa signature numérique est vérifiée pour s’assurer que le code provient d’une source authentifiée connue et que le code n’a pas été modifié depuis qu’il a été signé.

Dans le premier cas, vous faites confiance que l’application sera ne nuira pas et que vous faites confiance à l’origine de l’application. Dans la seconde, les signatures numériques sont utilisés pour vérifier l’authenticité. La signature numérique est un standard utilisé pour identifier et fournissent des informations sur le serveur de publication du code. Sa technologie est basée sur des normes, tels que RSA et X.509. En règle générale, les navigateurs permettent aux utilisateurs de choisir s’ils souhaitent télécharger et exécuter le code d’origine inconnue.

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)

