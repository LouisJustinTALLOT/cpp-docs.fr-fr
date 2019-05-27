---
title: Création de scripts pour l’enregistreur ATL
ms.date: 05/14/2014
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: f32606701ea08736985f0b0dd2ed82712040a049
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707058"
---
# <a name="creating-registrar-scripts"></a>Création de scripts d’enregistreur

Un script d’enregistreur fournit un accès basé sur les données (et non sur les API) au Registre système. L’accès basé sur les données est généralement plus efficace, car seulement une ou deux lignes sont nécessaires dans un script pour ajouter une clé au Registre.

L’[Assistant Contrôle ATL](../atl/reference/atl-control-wizard.md) génère automatiquement un script d’enregistreur pour votre serveur COM. Vous trouverez ce script dans le fichier .rgs associé à votre objet.

Le moteur de script de l’enregistreur ATL traite votre script d’enregistreur au moment de l’exécution. ATL appelle automatiquement le moteur de script lors de l’installation du serveur.

Cet article traite des sujets suivants associés aux scripts d’enregistreur :

- [Présentation de la syntaxe BNF (Backus Nauer Form)](../atl/understanding-backus-naur-form-bnf-syntax.md)

- [Présentation des arborescences d’analyse](../atl/understanding-parse-trees.md)

- [Exemples de scripts du Registre](../atl/registry-scripting-examples.md)

- [Utilisation de paramètres remplaçables (préprocesseur d’inscription)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [Appel de scripts](../atl/invoking-scripts.md)

## <a name="see-also"></a>Voir aussi

[Composant du Registre (enregistreur)](../atl/atl-registry-component-registrar.md)
