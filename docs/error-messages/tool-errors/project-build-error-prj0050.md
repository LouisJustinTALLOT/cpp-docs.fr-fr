---
title: Erreur de génération de projet PRJ0050
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: 56e092b5f7c33ad9543951621b2a9d8f6992331f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191988"
---
# <a name="project-build-error-prj0050"></a>Erreur de génération de projet PRJ0050

Échec de l’inscription de la sortie. Vérifiez que vous disposez des autorisations appropriées pour modifier le registre.

Le système C++ de génération visuel n’a pas pu enregistrer la sortie de la build (dll ou. exe). Vous devez avoir ouvert une session en tant qu’administrateur pour modifier le registre.

Si vous générez un fichier. dll, vous pouvez essayer d’inscrire manuellement le fichier. dll à l’aide de regsvr32. exe, qui affiche des informations sur la raison de l’échec de la Build.

Si vous ne générez pas de fichier. dll, recherchez dans le journal de génération la commande qui génère une erreur.
