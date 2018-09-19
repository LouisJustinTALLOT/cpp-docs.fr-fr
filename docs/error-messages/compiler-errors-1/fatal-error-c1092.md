---
title: Erreur irrécupérable C1092 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1092
dev_langs:
- C++
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9852b7b3d695d5414e52727ce672ee3258f6840b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077150"
---
# <a name="fatal-error-c1092"></a>Erreur irrécupérable C1092

Modifier & Continuer ne prend pas en charge les modifications sur les types de données ; génération requise

Vous avez modifié ou ajouté un type de données depuis la dernière build réussie.

- Modifier & Continuer ne prend pas en charge les modifications apportées aux types de données existants, notamment des définitions de classe, struct ou enum. Vous devez arrêter le débogage et générez l’application.

- Modifier & Continuer ne prend pas en charge l’ajout de nouveaux types de données si un fichier de base de données de programme, comme vc*x*0.pdb (où *x* est la version principale de Visual C++ en cours d’utilisation) est en lecture seule. Pour ajouter des types de données, le compilateur doit ouvrir le fichier .pdb en mode écriture.

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Pour supprimer cette erreur sans mettre fin à la session de débogage en cours

1. Replacez le type de données dans l’état où il se trouvait avant l’erreur.

1. Dans le menu **Déboguer** , choisissez **Appliquer les modifications du code**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Pour supprimer cette erreur sans modifier votre code source

1. Dans le menu **Déboguer** , choisissez **Arrêter le débogage**.

1. Dans le menu **Générer** , cliquez sur **Générer**.

Pour plus d’informations, consultez [Modifications de code prises en charge](/visualstudio/debugger/supported-code-changes-cpp).