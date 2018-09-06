---
title: Création de Scripts pour ATL (inscription) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abffe3c8d0a107c48c3a14a9bf584122229ad3b7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767258"
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

