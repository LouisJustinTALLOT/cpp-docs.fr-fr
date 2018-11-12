---
title: Création de Scripts pour ATL (inscription)
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: bc76e41ab0d2cd2d26ef227e6368cb420a8a6401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480236"
---
# <a name="creating-registrar-scripts"></a>Creating Registrar Scripts

Un script de bureau d’enregistrement fournit l’accès piloté par les données, plutôt que de piloté par les API, dans le Registre système. Accès piloté par les données est généralement plus efficace, car il accepte uniquement une ou deux lignes dans un script pour ajouter une clé au Registre.

Le [Assistant contrôle ATL](../atl/reference/atl-control-wizard.md) génère automatiquement un script de bureau d’enregistrement de votre serveur COM. Vous trouverez ce script dans le fichier .rgs associé à votre objet.

Moteur de Script d’inscription ATL traite votre script de bureau d’enregistrement en cours d’exécution. ATL appelle automatiquement le moteur de Script pendant l’installation du serveur.

Cet article traite des rubriques suivantes liées aux scripts de bureau d’enregistrement :

- [Présentation de la syntaxe BNF (Backus Nauer Form)](../atl/understanding-backus-nauer-form-bnf-syntax.md)

- [Présentation des arborescences d’analyse](../atl/understanding-parse-trees.md)

- [Exemples de scripts du Registre](../atl/registry-scripting-examples.md)

- [Utilisation de paramètres remplaçables (préprocesseur d’inscription)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [Appel de scripts](../atl/invoking-scripts.md)

## <a name="see-also"></a>Voir aussi

[Composant de Registre (inscription)](../atl/atl-registry-component-registrar.md)

