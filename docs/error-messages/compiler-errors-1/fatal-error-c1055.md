---
title: Erreur irrécupérable C1055
ms.date: 11/04/2016
f1_keywords:
- C1055
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
ms.openlocfilehash: e6df4870d7af49c369be7e513791955599c48326
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636506"
---
# <a name="fatal-error-c1055"></a>Erreur irrécupérable C1055

limite du compilateur : clés insuffisantes

Le fichier source contient trop de symboles. Le compilateur a manqué de clés de hachage pour la table de symboles.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Fractionnez le fichier source en fichiers plus petits.

1. Éliminer les fichiers d’en-tête.

1. Réutiliser des variables temporaires et globales au lieu de créer de nouveaux.