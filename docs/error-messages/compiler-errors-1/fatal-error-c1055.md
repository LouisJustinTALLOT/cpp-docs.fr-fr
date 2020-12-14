---
description: 'En savoir plus sur : erreur irrécupérable C1055'
title: Erreur irrécupérable C1055
ms.date: 11/04/2016
f1_keywords:
- C1055
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
ms.openlocfilehash: f85d3bc19b9dcd2ba3f4338e78c55cc7aa549fb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251646"
---
# <a name="fatal-error-c1055"></a>Erreur irrécupérable C1055

limite du compilateur : clés insuffisantes

Le fichier source contient trop de symboles. Le compilateur a manqué de clés de hachage pour la table de symboles.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Fractionner le fichier source en fichiers plus petits.

1. Éliminez les fichiers d’en-tête inutiles.

1. Réutilisez des variables temporaires et globales au lieu d’en créer d’autres.
