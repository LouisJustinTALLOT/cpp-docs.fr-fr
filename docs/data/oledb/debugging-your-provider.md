---
title: Débogage de votre fournisseur
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: e79719075bcd98733031abd63708bea861388cff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466212"
---
# <a name="debugging-your-provider"></a>Débogage de votre fournisseur

Il existe deux façons de déboguer votre fournisseur :

- Étant donné que les fournisseurs sont créés dans le processus, vous pouvez créer un code de consommateur à l’aide des modèles du consommateur OLE DB et l’étape dans le fournisseur normalement.

- Vous pouvez utiliser l’utilitaire ITEST fourni avec Visual C++.

## <a name="to-use-the-itest-utility"></a>Pour utiliser l’utilitaire ITEST

1. Ouvrez le projet de fournisseur.

1. Sur le **projets** menu, cliquez sur **paramètres**.

1. Dans le **Pages de propriétés** boîte de dialogue, cliquez sur le **déboguer** onglet.

1. Dans le **exécutable pour la Session de débogage** , sélectionnez l’application ITEST.

1. Définir des points d’arrêt et procédez au débogage comme d’habitude.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)