---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0050'
title: Erreur de génération de projet PRJ0050
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: 07a4df24f48a61e29214431840649566716bbac3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240804"
---
# <a name="project-build-error-prj0050"></a>Erreur de génération de projet PRJ0050

Échec de l’inscription de la sortie. Vérifiez que vous disposez des autorisations appropriées pour modifier le registre.

Le système de génération Visual C++ n’a pas pu enregistrer la sortie de la build (dll ou. exe). Vous devez avoir ouvert une session en tant qu’administrateur pour modifier le registre.

Si vous générez un fichier. dll, vous pouvez essayer d’inscrire manuellement le fichier. dll à l’aide de regsvr32.exe, ce qui doit afficher des informations sur la raison de l’échec de la Build.

Si vous ne générez pas de fichier. dll, recherchez dans le journal de génération la commande qui génère une erreur.
