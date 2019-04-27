---
title: Erreur de génération de projet PRJ0050
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: ec2490bad70d2b2eb72cbb48771900f09f8c2f67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226489"
---
# <a name="project-build-error-prj0050"></a>Erreur de génération de projet PRJ0050

Échec de l’inscription de la sortie. Vérifiez que vous disposez des autorisations appropriées pour modifier le Registre.

Le système de génération Visual C++ n’a pas pu enregistrer la sortie de la build (dll ou .exe). Vous devez avoir ouvert une session en tant qu’administrateur pour modifier le Registre.

Si vous générez un fichier .dll, vous pouvez essayer d’inscrire le fichier .dll manuellement à l’aide de regsvr32.exe, cela doit afficher des informations sur la raison pour laquelle la build a échoué.

Si vous ne créez pas un fichier .dll, examinez le journal de génération de la commande qui provoque une erreur.