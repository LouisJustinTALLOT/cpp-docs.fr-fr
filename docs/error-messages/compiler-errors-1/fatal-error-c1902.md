---
description: 'En savoir plus sur : erreur irrécupérable C1902'
title: Erreur irrécupérable C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: e41f1d6fa9e15f9ed748b6e916ef8d8dd314b3f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276086"
---
# <a name="fatal-error-c1902"></a>Erreur irrécupérable C1902

incompatibilité du gestionnaire de base de données du programme ; Vérifiez votre installation

Un fichier de base de données du programme (. pdb) a été créé à l’aide d’une version plus récente de mspdb *xxx*. dll que celle que le compilateur a trouvée sur votre système. Cette erreur indique généralement que mspdbsrv.exe ou mspdbcore.dll sont absents ou ont des versions différentes de mspdb *xxx*. dll. (L’espace réservé *xxx* dans le nom de fichier mspdb *xxx*. dll change avec chaque version de produit. Par exemple, dans Visual Studio 2015, le nom de fichier est mspdb140.dll.)

Assurez-vous que les versions correspondantes de mspdbsrv.exe, mspdbcore.dll et mspdb *xxx*. dll sont installées sur votre système. Assurez-vous que les versions incompatibles n’ont pas été copiées dans le répertoire qui contient le compilateur et les outils de liaison pour votre plateforme cible. Par exemple, vous avez peut-être copié les fichiers pour pouvoir appeler le compilateur ou l’outil de liaison à partir de l’invite de commandes sans définir la variable **d’environnement PATH** en conséquence.
