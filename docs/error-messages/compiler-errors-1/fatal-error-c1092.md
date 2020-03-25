---
title: Erreur irrécupérable C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: af43ddb83e872762f720b156644e0d466957a8a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203877"
---
# <a name="fatal-error-c1092"></a>Erreur irrécupérable C1092

Modifier & Continuer ne prend pas en charge les modifications sur les types de données ; génération requise

Vous avez modifié ou ajouté un type de données depuis la dernière génération réussie.

- Modifier & Continuer ne prend pas en charge les modifications apportées aux types de données existants, y compris les définitions de classe, de structure ou d’énumération. Vous devez arrêter le débogage et générer l’application.

- Modifier & Continuer ne prend pas en charge l’ajout de nouveaux types de données si un fichier de base de données de programme, tel que VC*x*0. pdb (où C++ *x* est la version principale de Visual utilisée) est en lecture seule. Pour ajouter des types de données, le compilateur doit ouvrir le fichier. pdb en mode écriture.

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>Pour supprimer cette erreur sans mettre fin à la session de débogage en cours

1. Replacez le type de données dans l’état où il se trouvait avant l’erreur.

1. Dans le menu **Déboguer** , choisissez **Appliquer les modifications du code**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Pour supprimer cette erreur sans modifier votre code source

1. Dans le menu **Déboguer** , choisissez **Arrêter le débogage**.

1. Dans le menu **Générer** , cliquez sur **Générer**.

Pour plus d’informations, consultez [Modifications de code prises en charge](/visualstudio/debugger/supported-code-changes-cpp).
