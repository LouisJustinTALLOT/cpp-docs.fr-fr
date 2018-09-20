---
title: 2.8 liaison de directives | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc5b702b17e01bb8d4625a837abdb71086113e68
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415900"
---
# <a name="28-directive-binding"></a>2.8 Liaison de directives

Liaison dynamique des directives doit respecter les règles suivantes :

- Le **pour**, **sections**, **unique**, **master**, et **barrière** directives lier à la dynamiquement englobant **parallèles**, s’il en existe, quelle que soit la valeur de n’importe quel **si** clause qui doivent être présent dans cette directive. Si aucune région parallèle n’est en cours d’exécution, les directives sont exécutées par une équipe composée du thread principal uniquement.

- Le **classés** directive lie à dynamiquement englobante **pour**.

- Le **atomique** directive applique un accès exclusif au niveau **atomique** directives dans tous les threads, pas seulement l’équipe actuelle.

- Le **critique** directive applique un accès exclusif au niveau **critique** directives dans tous les threads, pas seulement l’équipe actuelle.

- Une directive ne peut jamais lier dynamiquement à n’importe quelle directive en dehors de la plus proche englobante **parallèles**.