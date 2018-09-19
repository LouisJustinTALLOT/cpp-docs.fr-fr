---
title: Erreur de génération PRJ0050 de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb3949ea0db2f1667aecf1aeeefd922b192cbf41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100589"
---
# <a name="project-build-error-prj0050"></a>Erreur de génération de projet PRJ0050

Échec de l’inscription de la sortie. Vérifiez que vous disposez des autorisations appropriées pour modifier le Registre.

Le système de génération Visual C++ n’a pas pu enregistrer la sortie de la build (dll ou .exe). Vous devez avoir ouvert une session en tant qu’administrateur pour modifier le Registre.

Si vous générez un fichier .dll, vous pouvez essayer d’inscrire le fichier .dll manuellement à l’aide de regsvr32.exe, cela doit afficher des informations sur la raison pour laquelle la build a échoué.

Si vous ne créez pas un fichier .dll, examinez le journal de génération de la commande qui provoque une erreur.