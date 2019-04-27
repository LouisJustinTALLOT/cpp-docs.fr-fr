---
title: Erreur irrécupérable C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: c425430a6d08ae8a97c4dcd0f5764f44dee43e5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165864"
---
# <a name="fatal-error-c1902"></a>Erreur irrécupérable C1902

incompatibilité de gestionnaire de base de données de programme ; Veuillez vérifier votre installation

Un fichier de base de données de programme (.pdb) a été créé à l’aide d’une version plus récente de mspdb*XXX*.dll que celui que le compilateur a trouvé sur votre système. Cette erreur indique habituellement que mspdbsrv.exe ou mspdbcore.dll sont manquants ou ont des versions différentes de mspdb*XXX*.dll. (Le *XXX* espace réservé dans le mspdb*XXX*nom de fichier .dll change avec chaque version du produit. Par exemple, dans Visual Studio 2015, le nom de fichier est mspdb140.dll.)

Vérifiez les versions correspondantes de mspdbsrv.exe, mspdbcore.dll et mspdb*XXX*.dll sont installés sur votre système. Assurez-vous que les versions incompatibles n’ont pas été copiées dans le répertoire qui contient les outils du compilateur et le lien pour votre plateforme cible. Par exemple, vous pourrez copier les fichiers et ainsi vous pouvez appeler le compilateur ou l’outil link à partir de l’invite de commandes sans paramètre la **chemin d’accès** variable d’environnement en conséquence.